---
title: "Streaming urls in Xine and mplayer"
date: 2006-01-04
forum: General Help
---

### Post by yonkman on 2006-01-04
I have cable modem from [email]C@#$.net[/email].  The gave subscribers access live streaming hockey games this year.  FREE

I am stoked!!!!!  Almost a game a night!  worth the price of admission!!

But even on Cloud 9 a little rain falls.......

The are using mms to stream the games.  I was able, with much effort to get mpalyer installed.  It ONLY works with the upgraded mplayer plugin for firefox (I found the solution in the forums).

I want to try xine to see if it is a little less buggy, but I can't figure out how to "cut and paste" the url into xine to test.  URL's  just don't resolve correctly.

What is the best way to "translate" streaming media and secondly play it.  I think this is why the browser plugin is working because firefox must parse the media before sending it to mplayer.    

If I try to open the url in mplayer directly it errors saying it cannot translate it. ('cannot resolve name Af_inet6:www.comcast.net")

And ..... I cannot figure out how to "open URL" in xnie at all

What next should I be looking to do.


Thanks in advance  from 100% MS to 60% MS and counting.....

---

### Post by Zeddicus on 2006-01-04
I'm not all that experienced using the browser plugins themselves, but xine has always worked fine for streaming video/audio for me.

Have you tried just:

```
xine "mms://url.com/whatever"
```

Not ideal, but I've had good luck with it. :)

Also... that url looks... odd.  Shouldn't it be pointing to an actual file?

---

