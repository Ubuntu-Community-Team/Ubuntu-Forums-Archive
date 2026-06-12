---
title: "Screen Resolution - Feisty 7.04 - Compaq NC2400"
date: 2007-05-04
forum: Desktop Environments
---

### Post by Seb Spiers on 2007-05-04
Hi There,

I've just installed Ubuntu Feisty 7.04 on my HP Compaq NC2400 but can only select screen resolutions up to 1024x768.  The native resolution of the screen is 1280x800 so as you can imagine everything looks a bit stretched. :)

Can anyone tell me how I would go about changing to the native resolution. 

Thanks for your help. :-({|=

---

### Post by Breff on 2007-05-05
Try this link...

[http://ubuntuforums.org/showthread.php?t=424165&highlight=native+screen+resolution](http://ubuntuforums.org/showthread.php?t=424165&highlight=native+screen+resolution)

I have the same problem.  Haven't had time to try out their advice yet.  That's tomorrow's job!

---

### Post by Seb Spiers on 2007-05-06
> **Breff said:**
> Try this link...

[http://ubuntuforums.org/showthread.php?t=424165&highlight=native+screen+resolution](http://ubuntuforums.org/showthread.php?t=424165&highlight=native+screen+resolution)

I have the same problem.  Haven't had time to try out their advice yet.  That's tomorrow's job!Jet me know how you get on :)

---

### Post by ayoli on 2007-05-06
i had the same problem with my nc6400 with an intel I945GM graphics stucked at 1024x768 when native res is 1280x800, due to bad/absent BIOS messages that do not allow X to know the proper res
I've just 
```
sudo apt-get install 915resolution
```
(this package is in universe or multiverse repos) then i did:
```
gksudo gedit /etc/default/915resolution
```
and put these line:
```
MODE=3c
XRESO=1280
YRESO=800
BIT=24
```
then i've rebooted, and it now works like a charm.

---

### Post by Breff on 2007-05-06
Hi Seb,
I followed the instructions as per the link I sent you and I now have 1280x1024.  Nice!  It was very straightforward.  

Breff

---

### Post by Seb Spiers on 2007-05-06
> **ayoli said:**
> i had the same problem with my nc6400 with an intel I945GM graphics stucked at 1024x768 when native res is 1280x800, due to bad/absent BIOS messages that do not allow X to know the proper res
I've just 
```
sudo apt-get install 915resolution
```
(this package is in universe or multiverse repos) then i did:
```
gksudo gedit /etc/default/915resolution
```
and put these line:
```
MODE=3c
XRESO=1280
YRESO=800
BIT=24
```
then i've rebooted, and it now works like a charm.

Worked a dream, thanks dude.

---

### Post by tyr14 on 2007-10-05
**[COLOR="Navy"]Hi, i'm a new ubuntu user, somebody can teachme how to do this work, because i do not know nothin about linux, i'm really "new" thanx:lolflag::[/COLOR]**

i had the same problem with my nc6400 with an intel I945GM graphics stucked at 1024x768 when native res is 1280x800, due to bad/absent BIOS messages that do not allow X to know the proper res
I've just
Code:

sudo apt-get install 915resolution

(this package is in universe or multiverse repos) then i did:
Code:

gksudo gedit /etc/default/915resolution

and put these line:
Code:

MODE=3c
XRESO=1280
YRESO=800
BIT=24

then i've rebooted, and it now works like a charm.

---

### Post by ayoli on 2007-10-06
> **tyr14 said:**
> **[COLOR="Navy"]Hi, i'm a new ubuntu user, somebody can teachme how to do this work, because i do not know nothin about linux, i'm really "new" thanx:lolflag::[/COLOR]**
.
ok, open a terminal (Menu Accessories > Terminal) copy end paste this and hit enter:
```
sudo apt-get install 915resolution
```
(you 'll be prompted for your USER password because of sudo, enter hit and hit enter)
then, copy and paste this (with hiting enter after):
```
gksudo gedit /etc/default/915resolution
```
(you'll be again prompted for your user password in graphical mode this time)
when the text editor has opened the file find lines begining with these words:
```
MODE=
XRESO=
YRESO=
BIT=
```
There should have values after the eqaul sign, change these values to have this:
```
MODE=3c
XRESO=1280
YRESO=800
BIT=24
```
then save the file (CTRL+S or menu file > save), and reboot, that should be ok.

---

### Post by tyr14 on 2007-10-11
> **ayoli said:**
> ok, open a terminal (Menu Accessories > Terminal) copy end paste this and hit enter:
```
sudo apt-get install 915resolution
```
(you 'll be prompted for your USER password because of sudo, enter hit and hit enter)
then, copy and paste this (with hiting enter after):
```
gksudo gedit /etc/default/915resolution
```
(you'll be again prompted for your user password in graphical mode this time)
when the text editor has opened the file find lines begining with these words:
```
MODE=
XRESO=
YRESO=
BIT=
```
There should have values after the eqaul sign, change these values to have this:
```
MODE=3c
XRESO=1280
YRESO=800
BIT=24
```
then save the file (CTRL+S or menu file > save), and reboot, that should be ok.

[COLOR="Red"][B]I get this message: 

tyr@tyr-laptop:~$ sudo apt-get install 915resolution
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 915resolution[/B][/COLOR]

---

