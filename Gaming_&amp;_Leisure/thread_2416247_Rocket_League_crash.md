---
title: "Rocket League crash"
date: 2019-04-07
forum: Gaming &amp; Leisure
---

### Post by gedhaim on 2019-04-07
Hello! I've been trying to solve this problem for days, without success. 
When I start the game, generates a file dmp in /etc/tmp/dumps, but I can still play the game, for 1 min or even more, then crash and generates another dmp. I don't know how read these dmp files. 

output:
```
marco@marcolinux:~$ steam
Running Steam on ubuntu 18.10 64-bit
STEAM_RUNTIME is enabled automatically
Pins up-to-date!
[2019-04-08 01:28:25] Startup - updater built Feb 18 2019 22:08:53
[2019-04-08 01:28:25] Verifying installation...
[2019-04-08 01:28:25] Verification complete
crypto.cpp (2173) : Assertion Failed: rsaKey.IsValid()

```

but the strangest thing is that I played rocket league on linux, recently, on kubuntu and manjaro
I switched to arch from manjaro and when I tried rocket league... crash. I tried every single fix from arch wiki, didn't help. I thought it was arch the problem, so I switched again to ubuntu, but i'm using ubuntu minimal, with awesome wm.

what I tried in ubuntu:
without proprietary driver
with proprietary, nvidia 415 and 418
without compton
with another window manager, i3
DEBUGGER: gdb steam (but when I start rocket league with gdb, it freeze)
GAME_DEBUGGER: gdb steam (not useful, same output above)

any help? I'm new in linux, but I don't wanna back to windows lol awesome wm is simply...awesome.

---

### Post by poorpockets-mcnewhold on 2019-04-08
Couples of things I can suggest for you, Having personally fixed any issues I've had before (Except on strange inputs issues with controllers, but I won’t talk about that)
[LIST]
[*]Change your Steam Proton version, Several tests from other users has confirmed that it works under 3.16-* and 3.6-* versions, but in case, I would recommend you to test by yourself with the latest Proton version. [https://www.protondb.com/app/252950](https://www.protondb.com/app/252950)
[*]Try to add ```
-full-screen
``` launch setting, to preview crash when alt-tabbing.
[*]Verify your game cache, to verify that none of your files are missing or corrupted.
[/LIST]

---

### Post by gedhaim on 2019-04-08
> **poorpockets-mcnewhold said:**
> Couples of things I can suggest for you, Having personally fixed any issues I've had before (Except on strange inputs issues with controllers, but I won&#8217;t talk about that)
[LIST]
[*]Change your Steam Proton version, Several tests from other users has confirmed that it works under 3.16-* and 3.6-* versions, but in case, I would recommend you to test by yourself with the latest Proton version. [https://www.protondb.com/app/252950](https://www.protondb.com/app/252950) 
[*]Try to add ```
-full-screen
``` launch setting, to preview crash when alt-tabbing. 
[*]Verify your game cache, to verify that none of your files are missing or corrupted. 
[/LIST]


I tried all proton version, still crash.
-full-screen doesn't help
This is the strangest part lol because I already tried in arch to verify game file (also in ubuntu, ofc), but verify say "XXX files to validate and will be reacquired", downloading the whole game again, and when the download is complete, start over again, in loop. Not only with rocket league, but also with perfectly functioning games, like Limbo. The only way for fix the loop is uninstall the game and download again. 

Another strange thing: if I try to move rocket league to another library folder, it say "files can't be moved to new library folder (update required)", but I can move limbo. I compared the current BuildID with windows, 3676665, it is correct.
I installed steam with "sudo apt install steam" should I try with deb from steam site?

I think I found the problem, because the verify loop bug happens only with the library in the second hard drive, so now I'll download rocket league in the first hard drive (3 hours download lol)

---

### Post by oldrocker99 on 2019-04-08
If that works, that is some serious sleuthing on your part.

---

### Post by gedhaim on 2019-04-08
yep, it work .-. damn. probably the hard disk is going to die, end-to-end error failing, other value ok
maybe is related with my fstab?

```
# / was on /dev/sdc1 during installation
UUID=38d26ceb-ffb6-40c1-9b23-100b744aba2b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc2 during installation
UUID=75423dbf-67ff-44cd-9f9c-bead941e1aee none            swap    sw              0       0

/dev/sda2 /media/windows ntfs-3g defaults 0 0

/dev/sdc1 /media/storage ntfs-3g defaults 0 0


```

well I tried windows hard disk (sda2) and limbo fail, like in storage (sdc1) 
probably I need to fix fstab

fixed
/dev/sda2 /media/windows ntfs-3g uid=1000,gid=1000,rw,user,exec,umask=000 0 0
/dev/sdc1 /media/storage ntfs-3g uid=1000,gid=1000,rw,user,exec,umask=000 0 0

---

### Post by oldrocker99 on 2019-04-08
Gnome Disk Utility enables you to SMART test your HD.

---

### Post by gracemae on 2019-04-15
Wow thanks I thought ubuntu doesn't support it that's why I stop using it there, I might add SSD just for all the games.

---

