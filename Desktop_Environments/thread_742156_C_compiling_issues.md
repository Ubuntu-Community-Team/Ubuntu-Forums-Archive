---
title: "C compiling issues"
date: 2008-04-01
forum: Desktop Environments
---

### Post by bharadwaj on 2008-04-01
I have been trying to install ALSA.. so I downloaded the tar.bzs and then placed them where they belong to extracte them, and while compiling I was getting this error
```
bharadwaj@india-desktop:/usr/src/alsa/alsa-driver-1.0.16$ sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
[sudo] password for bharadwaj:
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```
I have a gcc for my job to be done regarding C..I have also worked on many programmes which went fine..I did almost everything I can but nothing seems to be working out..any help would be a gospel. Which would me to play Wine with sound
.:)

---

### Post by bharadwaj on 2008-04-01
Ah...just can't imagine how simple it was..
To solve this I had to install g++
And then when I tried again it worked, so to compile software with Linux it seems that you mostly need to install both

gcc and g++

And as usual I already have build-essentials already..so thought not to mention them ;)
:guitar:

---

