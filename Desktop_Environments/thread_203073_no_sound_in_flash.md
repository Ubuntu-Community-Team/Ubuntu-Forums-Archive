---
title: "no sound in flash"
date: 2006-06-24
forum: Desktop Environments
---

### Post by dguido on 2006-06-24
Does anyone have any idea why the sound in flash videos wouldn't work?  I'm using the flashplugin-nonfree package with Firefox in Dapper.  Youtube videos dont have sound.  I tried running update-flash with no luck.

---

### Post by aysiu on 2006-06-24
Maybe try this? ```
killall firefox
sudo aptitude update
sudo aptitude install alsa-oss
firefox
```

---

### Post by Ramses de Norre on 2006-06-24
You'll need to run firefox with "aoss firefox" or set "FIREFOX_DSP=" to aoss in /etc/firefox/firefoxrc.

---

### Post by Donshyoku on 2006-06-25
[QUOTE=Ramses de Norre]You'll need to run firefox with "aoss firefox" or set "FIREFOX_DSP=" to aoss in /etc/firefox/firefoxrc.[/QUOTE]

I am running Firefox with **FIREFOX_DSP="aoss"**, however, I am still having sound problems.  I am using the Flash plug-in from BUMPS and the latest Firefox as of today.

Any ideas?

---

### Post by dguido on 2006-06-30
Actually it was none of those.  All I did was 'killall esd', restarted firefox, and it worked fine!

Does anyone know why esd locks up /dev/dsp like that?  VMware has the same problem, no sound in virtual machines until I kill esd.  What the heck is esd good for?

---

### Post by harryhoudini66 on 2006-06-30
Hello,

I am a Linux newbie and have been using it for a week. I love it so far. After a considerable amount of research I finally got the sound to work as well as movies to play. 

Now I am trying to get sound on flash (Google video Youtube). I tried the above and cannot get it to work. I am sure it is User Error but just in case.

When I go back to check if the aoss change took place I see it did not. Can someone tell me step by step how to get the change to stick? Please leave no details out as I am sure I may be doing something wrong.

---

