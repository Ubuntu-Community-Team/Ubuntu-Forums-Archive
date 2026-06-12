---
title: "Ubuntu on Windows, Ubuntu installation not working."
date: 2008-12-14
forum: General Help
---

### Post by novabobogun on 2008-12-14
Hey everybody, 

So i recently received a Ubuntu 8.10 disk. I installed it on my pc using the "Install in Windows" option (I got a new PC that came with windows by default:-&, formatting the drive would be a waste)
Everything worked out and when I reboot everything was OK, I installed all the graphics drivers and the updates, no problem there. But then I saw that i only gave Ubuntu 9GB (half was used by system files, of course) and another 100-200mb by updates. Obviously 4.4GB was not enough for my tasking demands so I decided to reinstall Ubuntu (I found partionining to risky) When I placed my Ubuntu disc (after uninstalling) and selected the same options only this time instead of 9GB I selected 30GB, It installed the image and the other files. When I reboot there was no dual-boot, I tried rebooting but the dual-boot wasn't there. I then uninstalled and installed 3 times but it still didn't work...
Probably Windows took over the boot, EVIL WINDOWS....
Thanks for reading this post, if you have a solution PLEASE post it, I am extremely anxious to reinstall Ubuntu....

PS. I am currently using Windows Vista

---

### Post by bapoumba on 2008-12-15
Moved to Wubi.

---

### Post by Jammanuser on 2008-12-15
> **novabobogun said:**
> Hey everybody, 

So i recently received a Ubuntu 8.10 disk. I installed it on my pc using the "Install in Windows" option (I got a new PC that came with windows by default:-&, formatting the drive would be a waste)
Everything worked out and when I reboot everything was OK, I installed all the graphics drivers and the updates, no problem there. But then I saw that i only gave Ubuntu 9GB (half was used by system files, of course) and another 100-200mb by updates. Obviously 4.4GB was not enough for my tasking demands so I decided to reinstall Ubuntu (I found partionining to risky) When I placed my Ubuntu disc (after uninstalling) and selected the same options only this time instead of 9GB I selected 30GB, It installed the image and the other files. When I reboot there was no dual-boot, I tried rebooting but the dual-boot wasn't there. I then uninstalled and installed 3 times but it still didn't work...
Probably Windows took over the boot, EVIL WINDOWS....
Thanks for reading this post, if you have a solution PLEASE post it, I am extremely anxious to reinstall Ubuntu....

PS. I am currently using Windows Vista

hmm...i can't think of anything, sorry, other than downloading Wubi from [HERE]("http://www.wubi-installer.org/") and using it, instead of the CD. Probably, it would work then... ;)

Cheers! ):P

Jam Man

:guitar:

---

### Post by novabobogun on 2008-12-15
Thanks, I'll try Wubi, but the the whole installing off CD is still bugging me a little, I don't know if this makes sense but maybe Windows is trying to block it at start-up

---

### Post by novabobogun on 2008-12-15
Aarrgh,

Wubi is downloading slowly:-|......

---

### Post by ago on 2008-12-15
> **novabobogun said:**
> When I reboot there was no dual-boot, I tried rebooting but the dual-boot wasn't there. I then uninstalled and installed 3 times but it still didn't work...

There is a log in your user temp folder (%TEMP%), also check the bootloader settings (boot.ini in windows).

---

### Post by novabobogun on 2008-12-16
> **ago said:**
> There is a log in your user temp folder (%TEMP%), also check the bootloader settings (boot.ini in windows).

OK? What should I check in my temp file? I also couldn't find a boot.ini file in windows, even if I find it what do I do?

Anyways I'll try figuring it out, I'm not completely amateurish...

---

### Post by novabobogun on 2008-12-17
I tried downloading the iso off the ubuntu site, I mounted it with daemon tools, i installed it BUT IT STILL DOESN'T BOOT!
There is definitely something wrong with my system:-k .....

---

### Post by novabobogun on 2008-12-17
ago, I did a little researching on boot.ini, and if you haven't read my first post i said that i run vista, in vista they removed boot.ini....

---

### Post by novabobogun on 2008-12-18
I think I have a solution... GRUB was installed properly so the problem isn't that I'm thinking of copying the wubuilder file from ubuntu into my boot folder, now all I need now are administrative privileges.  By the way someone tell me if what i am doing is risky because I'm messing with my boot....

---

### Post by ago on 2008-12-19
For vista you need to use EasyBCD.
Note that there is a wubi log in your user temp folder.
Also note that wubi installs grub4dos (and specifically c:\wubildr and c:\wubildr.mbr) the Windows bootloader has to pointo to wubildr.mbr

---

### Post by bapoumba on 2009-01-10
Moved to General Help, per OP's request.

---

### Post by novabobogun on 2009-01-18
I`ll see if that works, ago, if it doesn`t and i mess up my system I`ll blame it on you ;)

---

