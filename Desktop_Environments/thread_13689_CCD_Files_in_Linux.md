---
title: "CCD Files in Linux"
date: 2005-02-02
forum: Desktop Environments
---

### Post by arnoct on 2005-02-02
I'm trying to burn CCD (CloneCD) files (namely psone games; yes, I'm a pirate) but I have not found a way to burn them through Linux. I tried ccd2iso, however the CD did not work properly after conversion. Is there an easy way to burn CCD files directly? I wouldn't want to get rid of ubuntu for a silly thing like not being able to burn CCDs (I can't dualboot, so it's all or nothing for me :P)

---

### Post by AndersAA on 2005-02-02
I ran nero in wine for a while, and that worked flawlessly, could try a solution like that.

---

### Post by arnoct on 2005-02-03
Hmm. I have nero running on WINE, but I can't get it to see my CDRW drive... The console output is giving me some ASPI error; is there a problem or am I just doing something wrong?

---

### Post by AndersAA on 2005-02-03
[QUOTE=arnoct]Hmm. I have nero running on WINE, but I can't get it to see my CDRW drive... The console output is giving me some ASPI error; is there a problem or am I just doing something wrong?[/QUOTE]

no idea sorry, I ran it a few ages and and it worked fine, might wanna try googling it.

---

### Post by Kotts on 2005-02-03
[QUOTE=arnoct]Hmm. I have nero running on WINE, but I can't get it to see my CDRW drive... The console output is giving me some ASPI error; is there a problem or am I just doing something wrong?[/QUOTE]

Wine is very much a work in progress.  Which version of Wine are you running (if you know)?

I have had the best success compiling Wine from source, rather than using a package, but bear in mind that it may take tweaking or access to "native" windows dll files to get some programs to work.

Nero is such common windo$e software that I suspect that the problem has already found a resolution.  If you want to pursue this option, I'd suggest hooking up with the folks at [www.winehq.org](www.winehq.org) and subscribing to some of the mailing lists there.  

Kotts

---

### Post by arnoct on 2005-02-04
Thanks for the advice; I'll try signing up for some of the mailing lists at winehq. I was trying to run the latest version from warty-backports. There are many reports of the software working, so I know people have gotten it to work; it just doesn't see my drive. According to [this page](http://frankscorner.org/index.php?p=nero6), Nero 6.0.0.9 (the version I'm trying to install,) works fine on WINE, but it says "If Nero has problems finding your cd/dvd writer there is probably a permission problem. Make sure it has read/write permissions to the writer. " I had a friend SSH into my computer, but he couldn't figure it out, either :(

I'll also try compiling from source.

---

### Post by fakie_flip on 2007-04-15
> **AndersAA said:**
> I ran nero in wine for a while, and that worked flawlessly, could try a solution like that.

There is a Linux version of Nero, so you don't need Wine.

---

