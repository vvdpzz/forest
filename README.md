# Group

## News
like `Hacker News `  

    (= gravity* 1.8 timebase* 120 front-threshold* 1
            nourl-factor* .4 lightweight-factor* .17 gag-factor* .1)
    (def frontpage-rank (s (o scorefn realscore) (o gravity gravity*))
        (* (/ (let base (- (scorefn s) 1)
                (if (> base 0) (expt base .8) base))
            (expt (/ (+ (item-age s) timebase*) 60) gravity))
            (if (no (in s!type 'story 'poll))  .8
                (blank s!url)                  nourl-factor*
                (mem 'bury s!keys)             .001
                                            (* (contro-factor s)
                                                (if (mem 'gag s!keys)
                                                    gag-factor*
                                                    (lightweight s)
                                                    lightweight-factor*
                                                    1)))))

## Q&A
like `stackoverflow` & `quora`

## Wiki
like `github wiki`

##  Whisper
like `campfire`, open API, show some notifications when something happened

## History
like `Path 2`, a timeline