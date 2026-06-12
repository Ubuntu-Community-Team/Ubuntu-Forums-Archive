---
title: "This is going to be a stupid question..."
date: 2009-06-04
forum: General Help
---

### Post by akakingess on 2009-06-04
I have read documentation, I am reading books, beginners guides, trying help although in Karmic Alpha it keeps crashing on me, but my question is so simple i feel ignorant. I have downloaded the flash player and plugin and unpacked it, and read the read me file, but still can't figure out how to run or what command to use to execute flashplayer-installer, not to mention getting all the plugins where they go. Could someone please just post a link or a simple one line explanation.  maybe there is more wrong with my Alpha build than i thought, in which case I will just roll back to Jaunty. Thank you in advance if you bother to help such a silly question. I promise I have searched and read and re-read, I am just overlooking one thing, i think.

akakingess

---

### Post by pawnrocket on 2009-06-04
```
sudo ./nameofinstallerscript
```

I will also say this. Install a usable OS. My pick is Ubuntu 8.04 ... On another partition install Karmic ... Test all you want, but don't get so pissed that you stop using it and install over it. Keep a copy... when you get stressed load your stable OS.

---

### Post by ibuclaw on 2009-06-04
Have you ran the following in same directory as the installer script?
```
sh flashplayer-installer
```

If you install it **without** the use of sudo, it will install the plugin inside your ~/.mozilla directory, making it accessible as soon as you close, and restart firefox.

Regards
Iain

---

### Post by pawnrocket on 2009-06-04
> **tinivole said:**
> Have you ran the following in same directory as the installer script?
```
sh flashplayer-installer
```

If you install it **without** the use of sudo, it will install the plugin inside your ~/.mozilla directory, making it accessible as soon as you close, and restart firefox.

Regards
Iain

I am brain fried

---

### Post by rcayea on 2009-06-04
As a teacher, I feel the need to tell you that no question is stupid and believe or not, someone down the line will one day come upon this post and find it helpful. :)

---

### Post by akakingess on 2009-06-04
i had tried that, also, I didn't write over Jaunty, this (Karmic) is on a different drive, just to try out. Definitely will keep updating it and trying it out every other day or so.  I love Jaunty and have 0 problems with it. Thanks for the tips, I could swear I tried it both ways suggested, but maybe I was mistaken. Thanks for the quick responses.

akakingess

---

### Post by ibuclaw on 2009-06-05
Close all instances of Firefox, then run:
```
mkdir -p ~/.mozilla/plugins
mv libflashplayer.so ~/.mozilla/plugins

```

Then start firefox, open a new tab and enter in:
```
about:plugins
```
And you should see "**Shockwave Flash**" as a title in that list.


Regards
Iain

---

### Post by d4x2hhhy on 2009-06-05
I know how you feel but this is useful already!

Im trying to run the ALSA upgrade script : AlsaUpgrade-1.0.x-rev-1.17.sh which i unpacked from .tar.  How do I run this please?  its sitting on my desktop

---

### Post by d4x2hhhy on 2009-06-05
ok used the sudo ./xxxx  cheers

---

