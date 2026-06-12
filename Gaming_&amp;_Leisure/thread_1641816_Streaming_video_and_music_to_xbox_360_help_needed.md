---
title: "Streaming video and music to xbox 360? help needed"
date: 2010-12-09
forum: Gaming &amp; Leisure
---

### Post by o0o Wiggy o0o on 2010-12-09
Hi Guys,

This is the only thing stopping me from totally coming to Ubuntu rather  than dual booting with Windows 7.....i need help sharing my Videos and  Music to the XBOX 360....i'm new to Linux but i love it so if i can get  this resolved i would be a very happy Linux user.

Regards

---

### Post by thatguruguy on 2010-12-09
You can stream video and audio to xbox 360 with coherence  (a DLNA/UPnP server).  Look for "gcoherence" in synaptic or the Software Center.

---

### Post by racie on 2010-12-10
Yep, here's the website for it just to convince you: [http://29a.ch/gcoherence/](http://29a.ch/gcoherence/)

And here are some alternatives:
[http://strawp.net/archive/streaming-media-from-linux-to-a-games-console/](http://strawp.net/archive/streaming-media-from-linux-to-a-games-console/)

---

### Post by thatguruguy on 2010-12-10
> **sunnynice said:**
> gcoherence? sure for that??

I don't know what "sure for that" means, so I can't help you.  Maybe you should post whatever question you have in a different thread.

---

### Post by caseyweederman on 2010-12-10
the gcoherence install tries to download a non-existent file.
The backup url:
[http://pypi.python.org/packages/2.6/s/setuptools/setuptools-0.6c8-py2.6.egg](http://pypi.python.org/packages/2.6/s/setuptools/setuptools-0.6c8-py2.6.egg)
is a dead link.
The softpedia download is a dead link.
Synaptic as of Ubuntu 10.04 has no such file.
Firefox doesn't trust the site linked on the gcoherence front page.

How, pray tell, does one acquire this program?

---

### Post by racie on 2010-12-10
Try some of the alternative programs in this link: [http://strawp.net/archive/streaming-media-from-linux-to-a-games-console/](http://strawp.net/archive/streaming-media-from-linux-to-a-games-console/)

---

### Post by o0o Wiggy o0o on 2010-12-11
Thank you i'll test it out and report back. Cheers

---

### Post by racie on 2010-12-11
Good luck.

---

### Post by caseyweederman on 2010-12-11
blep's fix here:
[https://bugs.launchpad.net/launchpadlib/+bug/406366](https://bugs.launchpad.net/launchpadlib/+bug/406366)
solves the problem. Overwrite the ez_setup.py file in your gcoherence folder and then run the install as per the README.
Gcoherence works great, I successfully watched an avi *from the other room!* It was great.
Thanks to this thread and blep's fix for the help!

edit: gcoherence I got from [http://29a.ch/gcoherence/](http://29a.ch/gcoherence/)

---

### Post by o0o Wiggy o0o on 2010-12-12
> **caseyweederman said:**
> blep's fix here:
[https://bugs.launchpad.net/launchpadlib/+bug/406366](https://bugs.launchpad.net/launchpadlib/+bug/406366)
solves the problem. Overwrite the ez_setup.py file in your gcoherence folder and then run the install as per the README.
Gcoherence works great, I successfully watched an avi *from the other room!* It was great.
Thanks to this thread and blep's fix for the help!

Where did you get gcoherence from in the end?

---

### Post by caseyweederman on 2010-12-12
gcoherence from: [http://29a.ch/gcoherence/](http://29a.ch/gcoherence/)
ez_setup from the first comment: [https://bugs.launchpad.net/launchpadlib/+bug/406366](https://bugs.launchpad.net/launchpadlib/+bug/406366)
[=http://peak.telecommunity.com/dist/ez_setup.py](direct link to ez_setup.py)](=http://peak.telecommunity.com/dist/ez_setup.py](direct link to ez_setup.py))

---

### Post by Rikeshar on 2011-04-03
- post deleted -

---

