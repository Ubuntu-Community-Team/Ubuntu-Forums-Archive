---
title: "Firefox plug-in....Quicktime?"
date: 2006-03-09
forum: Desktop Environments
---

### Post by chris_andrew on 2006-03-09
Hi,

I'm trying to view the animated clips at:

[http://www.pixar.com/theater/shorts/ftb/index.html](http://www.pixar.com/theater/shorts/ftb/index.html)

I get a Totem error when I use Firefox.  I note from the plug-ins preferences that Quicktime support is available.  What can i do to get it to work?

Any ideas?

Thanks,

Chris.

---

### Post by kaamos on 2006-03-09
Works fine for me with mozilla-mplayer

---

### Post by chris_andrew on 2006-03-09
Hmm,

Is that in the standard repositories?  Is it free software?

Thanks,

Chris.

---

### Post by kaamos on 2006-03-09
Its Free. Seems to be in multiverse: [http://packages.ubuntu.com/breezy/misc/mozilla-mplayer](http://packages.ubuntu.com/breezy/misc/mozilla-mplayer)

I have a different version, I don't think that matters. Imho mplayer does a better job with most files than totem, so I suggest you try that.

---

### Post by TZRick on 2007-06-02
Same problem here and I have mozilla-mplayer installed.  When I pull up the pixar site ([http://www.pixar.com/theater/shorts/ftb/index.html](http://www.pixar.com/theater/shorts/ftb/index.html)), I see a media toolbar with a slider, as if the movie is about to begin, but nothing happens. The slider does not move and the movie does not play.

Any ideas?

---

### Post by TZRick on 2007-06-03
Thanks for your immense feedback on this topic.  Really nice group of people here.

In any case, I was able to get things fixed.  I uninstalled all the junk I tried and reinstalled mplayer and mplayer-mozilla and everything worked.  I had the the codecs installed from before.

---

### Post by David Mulligan on 2007-06-03
I got the Pixar animations to work well but I cannot get Apple ads to show.  The Apple iPhone ads are at [http://www.apple.com/iphone/ads/](http://www.apple.com/iphone/ads/)

Can any of you see these?  When I try to watch them I see the mplayer plug-in and the video start to buffer but it fails to get to 100 and then the plug-in goes away.  Of course I could not find anything written to any log file to explain the failure either.

Thanks,
David

---

### Post by yeshuadoom on 2007-06-04
I'm having this same problem.

---

### Post by jtp51 on 2007-06-04
Seems to me that all Apple.com QuickTime Movie trails are working. Maybe the iPhone QuickTime ads have some interactive sections at the end that might cause MPlayer not to play them?

:?:

---

### Post by TZRick on 2007-06-04
Same problem here.  I think there is some sort of size limit issue though.  If you try loading the various clips (Small, Medium, Large, HD), you will notice that the Small loads the furthest, Medium loads less, and so on.  So it seems to me to be a limit in some buffer, as David hinted to.

---

