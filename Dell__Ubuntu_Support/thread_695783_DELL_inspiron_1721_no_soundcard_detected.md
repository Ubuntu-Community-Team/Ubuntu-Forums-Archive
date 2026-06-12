---
title: "DELL inspiron 1721 no soundcard detected"
date: 2008-02-13
forum: Dell  Ubuntu Support
---

### Post by Dokus on 2008-02-13
I have a problem in getting my sound to work, when I tried "asoundconf list" I didn't get any sound cards. 
and alsa ain't working. How could i access my sound card? I'm in kubuntu gutsy on a dell inspiron 1721.
anyone else seen a solution?

---

### Post by ymmatt on 2008-02-14
I have the same machine and after alot of messing around with other issues like the wirless my audio works.

It may have been this:
> Next for sound you need to do sudo apt-get install linux-backports-modules-generic and then reboot. I do not know what this does but it made my sound work.

From this post:
[http://ubuntuforums.org/showthread.php?t=598314](http://ubuntuforums.org/showthread.php?t=598314)

Another user stated that doing: ```
sudo apt-get remove alsa
``` helped, but I didn't need this.

In the end don't assume it isn't working, the volume may be way too low. run kmix and increase the volume until you hear it.

Hope this helps.

---

### Post by Dokus on 2008-04-08
Ok It helped me a lot finally I can hear again some nice :guitar:

Thanks

---

