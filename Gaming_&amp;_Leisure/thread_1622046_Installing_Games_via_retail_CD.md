---
title: "Installing Games via retail CD?"
date: 2010-11-15
forum: Gaming &amp; Leisure
---

### Post by SbKhaan1 on 2010-11-15
I have an old windows game here (Black & White 2) that takes up about 4 cd's here, and i wanted to see if i can run it on my ubuntu. I'm in 10.10 and i figure since i have wine installed the game should be tricked into thinking i have a C drive and install normally, so i go into the CD and into permissions and try to give it permissions to execute, but it gives me..

> Sorry, could not change the permissions of "Setup.exe": Error setting permissions: Read-only file systemsAnyway i can bypass this and change permissions?

---

### Post by amauk on 2010-11-15
you can't "change" anything on a CD, as it's a read-only medium

Just double click the setup file, and wine should fire up

---

### Post by SbKhaan1 on 2010-11-15
It tries to open Archive Manager, so i right-click and open with WINE and it says the media file is not marked as an executable, which brings me back to my original issue.

---

### Post by amauk on 2010-11-15
Try this,
open up a terminal, and do
```
wine /cdrom/Setup.exe
```

---

### Post by SbKhaan1 on 2010-11-15
Command not found.-

---

### Post by amauk on 2010-11-15
do you have wine installed?

---

### Post by SbKhaan1 on 2010-11-15
Yeah, wine 1.2.

Do i need 1.3?

---

### Post by amauk on 2010-11-15
no, any version will do,
but you said you're getting command not found?

Can you post the exact error

---

### Post by SbKhaan1 on 2010-11-15
wow, thats weird. If i type the command i get 'Command Unknown'

if i paste it i get this...

> wine: cannot find '/cdrom/Setup.exe'

It cant find my setup.exe?

---

### Post by amauk on 2010-11-15
oh, ok
so the cd drive isn't mounted in /cdrom

try /media/cdrom

---

### Post by SbKhaan1 on 2010-11-15
Heheh.. i'm supposed to put the name of the cd in place of "cdrom" right?

---

### Post by SbKhaan1 on 2010-11-15
Okay, i found the directory, i found it with this..


> john@john-KC834AV-ABA-s3300z:~$ cd /media
john@john-KC834AV-ABA-s3300z:/media$ ls
COD2CD1
john@john-KC834AV-ABA-s3300z:/media$ cd /COD2CD1
bash: cd: /COD2CD1: No such file or directory
john@john-KC834AV-ABA-s3300z:/media$ cd COD2CD1
john@john-KC834AV-ABA-s3300z:/media/COD2CD1$ ls
00000001.TMP  2057.mst     Docs          instmsiw.exe   SECDRV.SYS  Splash.bmp
0x0409.ini    autorun.inf  DrvMgt.dll    ISScript9.Msi  Setup       version.inf
0x0809.ini    COD2.msi     Extras        Launch.exe     setup.exe
1033.mst      DirectX      instmsia.exe  Launch.ini     Setup.ini
john@john-KC834AV-ABA-s3300z:/media/COD2CD1$ wine setup.exe

But afterwards it gave me a huge list of errors which i didn't catch, but it still ran. I tried it again and i got no errors. Strange, i guess it doesn't matter? I'll try to install it now and post back if something goes wrong.

---

### Post by nlsthzn on 2010-11-15
Would suggest installing Playonlinux (in Software Center) and seeing if Black and White is supported... if it is just follow the prompts... Good luck!

---

### Post by SbKhaan1 on 2010-11-15
Installing it directly through terminal gives me

> Error: -1603 Fatal error occurred during installation.

I'll try PlayOnLinux.

---

