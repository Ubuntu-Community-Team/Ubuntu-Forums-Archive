---
title: "No sound in Flash movies/Flash content"
date: 2006-07-05
forum: Desktop Environments
---

### Post by darthvivi on 2006-07-05
I have the Flash plugin, and Flash content loads properly, but I don't get any sound. I've tried to get sound on Opera and Firefox, but it doesn't work on either of them.

I know the sound on my system is working properly, because I can listen to music in Rhythmbox. So any idea why it does this?

---

### Post by DJ Scribblinni on 2006-07-05
The reason for that would be the version that Macromedia allows us linux people to have.  Windows and Apple have version 7.5 I believe.  Linux is stuck with 7.  Sounds and some visual cues are the differences that we see.  As far as I know, until the next version comes out, we are stuck...

---

### Post by darthvivi on 2006-07-05
Heh, sorry, I should have searched better. I fixed it with:
```

sudo apt-get install alsa-oss
```

Then restarted Firefox

---

### Post by morguns on 2006-07-05
See post #5 by Corvillus in:
[http://www.ubuntuforums.org/showthread.php?t=187752](http://www.ubuntuforums.org/showthread.php?t=187752)```
ln -s /tmp/.esd-1000 /tmp/.esd
```Worked like a champ for me.

---

### Post by Hagbarddenstore on 2006-07-07
Hey... What about Opera then? I hate using Firefox... Opera is my thing... But i don't have sound i think... installing Flash as we speak... I use Kubuntu and ALSA all the way! =)

---

### Post by richbarna on 2006-07-07
> **darthvivi said:**
> I have the Flash plugin, and Flash content loads properly, but I don't get any sound. I've tried to get sound on Opera and Firefox, but it doesn't work on either of them.

I know the sound on my system is working properly, because I can listen to music in Rhythmbox. So any idea why it does this?

I found this on launchpad
>  sudo aptitude install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

change: FIREFOX_DSP="none"
to: FIREFOX_DSP="aoss"

repeat for: /etc/mozilla-firefox/mozilla-firefoxrc

---

### Post by emkay_de on 2008-06-12
View my post to solve "opera flash no sound problem"

[http://ubuntuforums.org/showthread.php?t=186594&page=6](http://ubuntuforums.org/showthread.php?t=186594&page=6)

cu

---

