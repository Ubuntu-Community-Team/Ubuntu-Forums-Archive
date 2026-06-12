---
title: "Can't get FB games to load"
date: 2013-10-04
forum: Gaming &amp; Leisure
---

### Post by Bryan11 on 2013-10-04
Hi Guy's,
             I finally got around to installing 12.04 after ditching 'mate' only to find there's noway I can get facebook games to load. I even did a sudo to get x11 which I got from a comment on the flash installer page in the software centre. I have tried the firefox and chrome browsers but no way will ANY game load. To check on my hardware I put a liveCD of precise puppy in and had no problems. One would think out of the box 12.04 should just plain work with facebook games but alas it isnt so.

Any help on this will be greatly appreciated too.

Regards Bryan

---

### Post by Bryan11 on 2013-10-04
OK Guy's,
                Finally found the flash plugin installer  in usr/lib but noway can I get it to run. It may sound like a stupid Q  to you guys but it has been a few years since I used linux and the grey  matter is having fun trying to remember all the shell commands.
 Below is snippet from the terminal and trying make says theres nothing to make, dpkg also does nothing so I am at loss here.
 
/usr/lib/flashplugin-installer$ ls
install_plugin  libflashplayer.so

 
Regards Bryan

---

### Post by gregz41 on 2013-10-05
I have the very same problem.... I have found that linux does not like to play flash games. i have been playing around with linux since open suse and never had one play a flash game out of the box so to speak.... I interested in this let me know if u fix it...

---

### Post by drarem2 on 2013-10-20
Get chromium-browser and the libpepper library (or pepper?).. since google and flash have some agreement to continue support. Adobe only provides security updates for firefox. Personally adobe is killing off flash in my opinion, although it's doing a good job by itself.

---

### Post by drarem2 on 2013-10-20
Pogo games suck for that very reason, don't get sucked into a user account. There are frequent breaks in flash,  have to keep the google browser in sync.

---

### Post by dannyboy79 on 2013-10-20
> **Bryan11 said:**
> OK Guy's,
                Finally found the flash plugin installer  in usr/lib but noway can I get it to run. It may sound like a stupid Q  to you guys but it has been a few years since I used linux and the grey  matter is having fun trying to remember all the shell commands.
 Below is snippet from the terminal and trying make says theres nothing to make, dpkg also does nothing so I am at loss here.
 
/usr/lib/flashplugin-installer$ ls
install_plugin  libflashplayer.so

 
Regards Bryanthat's the flash file itself, there's nothing to install. you merely can copy it to the other browser folders that are applicable. I am using Xubuntu 12.04.3 with Google Chrome version Version 30.0.1599.101 and I have no problem playing FB games. I have that file only in 1 location, which is 
```
/usr/lib/flashplugin-installer/libflashplayer.so
```

Actually I just looked within aptitude and the ubuntu software center and I can't find anything with libflashplayer so I am not sure what's going on. LMFAO

---

### Post by vegan.philosophy on 2013-11-02
Have you tried to clear cache and cookies of your web browser?

---

