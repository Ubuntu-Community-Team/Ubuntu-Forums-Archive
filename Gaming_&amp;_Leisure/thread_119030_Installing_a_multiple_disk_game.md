---
title: "Installing a multiple disk game"
date: 2006-01-18
forum: Gaming &amp; Leisure
---

### Post by ianl on 2006-01-18
Hi again,

I know for a fact this has been covered before, I read the thread a while ago, before I needed to use it, and I can't find it again.

I'm trying to install WoW from four cd's, installing from the first is fine to c:/program files, or to my home dir. But when I need the second cd, I insert it but the installer won't recognise it, I can just keep on the clicking the "Insert CD 2" dialogue but nothing happens. I have detected both my cd drives in winecfg, and done all that stuff, I have tried to mount from root with 'sudo mount /media/cdrom' but it says it is already mounted.  The cd contents are also definitely showing up when I browse it.

Any help would be appreciated, thanks.

EDIT: Also, I don't have a Windows partition to copy the game off of :)

---

### Post by alynx on 2006-01-19
[QUOTE=ianl]Hi again,

I know for a fact this has been covered before, I read the thread a while ago, before I needed to use it, and I can't find it again.

I'm trying to install WoW from four cd's, installing from the first is fine to c:/program files, or to my home dir. But when I need the second cd, I insert it but the installer won't recognise it, I can just keep on the clicking the "Insert CD 2" dialogue but nothing happens. I have detected both my cd drives in winecfg, and done all that stuff, I have tried to mount from root with 'sudo mount /media/cdrom' but it says it is already mounted.  The cd contents are also definitely showing up when I browse it.

Any help would be appreciated, thanks.

EDIT: Also, I don't have a Windows partition to copy the game off of :)[/QUOTE]

Hi 

Make a new directory called feks: WOWINSTALL 
Copy all the files from all 4 cd's into that directory.
Then execute the command : wine Installer.exe

The installation willl now run without prompting you for any cd's.

:razz:

---

### Post by alynx on 2006-01-25
well , how did it go mate ?

---

### Post by alynx on 2006-02-08
i guess it turned out well , since you haven't checked in on your thread ;)

---

