---
title: "Flash problem"
date: 2006-09-24
forum: Desktop Environments
---

### Post by grontoft on 2006-09-24
Hi there!

I'm having a problem with sounds in flash. When I try to play a media file, for example google videos, I get no sound.

Is there any way to fix this problem?

---

### Post by minisori on 2006-09-24
odd i seem to have the same problem, since the last firefox update. I'll check on it.

---

### Post by r4ik on 2006-09-24
From   [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Try,

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

    * Restart Mozilla Firefox. Now sound should work in Flash Player. 


Hope it helps.
Good luck.

---

### Post by grontoft on 2006-09-24
r4ik:

Thanks a lot, that helped a lot!

---

### Post by r4ik on 2006-09-24
You're welcome.
Thanks for the reply.

---

