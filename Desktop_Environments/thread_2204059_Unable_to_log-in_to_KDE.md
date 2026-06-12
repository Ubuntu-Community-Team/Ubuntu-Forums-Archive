---
title: "Unable to log-in to KDE"
date: 2014-02-06
forum: Desktop Environments
---

### Post by petermylward on 2014-02-06
Hi There,

I am having problems with KDE. I have a dreaded AMD Radeon HD 4600 - and had less than stellar results getting this to work on anything other than a really old kernel - which I wasn't happy going on with for security reasons now it is getting on a bit.

I had then gone from 12.04 to 13.10 unity and had very little joy - I had installed KDE manually and it worked out of the box using the xorg-edgers driver.

So - bright spark decided to install a fresh Kubuntu 13.10 image  - guess what it now doesn't work :'(

My Xorg.0.log file is only giving me the usual EE of module fglrx not found - but it is loading the edgers driver fine after that.
.zsession-errors only has 2 lines in it

```
Script for cjkv started at run_im.
Script for default started at run_im.
```

I do not have a kde.log file in /var/log or on the entire drive which is odd.

I logon - get the splash screen which loads up an icon or 2 and then freezes - half blurred out. the mouse and keyboard is still responsive. I have tried to export display from tty and kwin --replace, tried ccsm, I can't think of where to go next - any help would be much appreciated - even help in finding the log I should be looking at to get a leg up on where to look.

Many thanks

---

### Post by petermylward on 2014-02-07
Sorry to bump this, but does anyone have any ideas?

---

### Post by lz1dsb on 2014-02-07
Have you tried to remove the fglrx driver? Recently after an update my fglrx driver broke. I logged into the system, purged it, and than I installed an older version which works for me. This solved it....

---

### Post by petermylward on 2014-02-07
Thanks lz, part of the reason to fresh install was to clean up all the driver shenanigans, so I haven't actually installed fglrx this time round - I went straight from stock open source to edgers. I think Xorg looks for it by default first, I've read elsewhere this is common, but not certain.

---

### Post by Bashing-om on 2014-02-07
petermylward; Hey;

Sorry that I must be the bearer of sad news.

> 
 AMD Radeon HD 4600

No OEM support !
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)


If fglrx drivers are a requirement, then installing version 12.04.1 is the better solution.

Else: open source driver for the duration !

[INDENT][INDENT]some things
[INDENT][INDENT]beyond our control
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lz1dsb on 2014-02-07
I have Mobility Radeon HD 4530 on my Dell Studio 1555 machine. The latest possible version which is usable for me is 12.6 of the ATI Drivers. I downloaded it about a year ago from ATI's site and it's considered to support legacy video cards.

---

### Post by petermylward on 2014-02-07
OK - thanks both, either downgrade or new card then!

---

### Post by Bashing-om on 2014-02-07
petermylward; Hey, Not so fast !

Might try version 13.10; has enhanced support with open source drivers for older graphics cards. You may be pleasantly surprised. 

The developers have put a lot of effort into this aspect and have come a long way with open source drivers.

[INDENT][INDENT]certainly worth considering
[/INDENT][/INDENT]

---

### Post by Erik1984 on 2014-02-08
> **Bashing-om said:**
> petermylward; Hey, Not so fast !

Might try version 13.10; has enhanced support with open source drivers for older graphics cards. You may be pleasantly surprised. 

The developers have put a lot of effort into this aspect and have come a long way with open source drivers.
[INDENT][INDENT]certainly worth considering
[/INDENT]
[/INDENT]


Seems like he tried that already:

from OP:
> fresh Kubuntu 13.10 image

---

