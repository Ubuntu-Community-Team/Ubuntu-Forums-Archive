---
title: "UT2004 install?"
date: 2004-12-14
forum: Gaming &amp; Leisure
---

### Post by nastynate on 2004-12-14
howdy all .. . i just installed ubuntu 4.10 and aside from apt not working everything seems ok (updates work via the gui frontend ..  no idea how to fix apt : /  )  but i get a permission denied error when i try to run the UT linux installer as user or root.. i double checked and i know i have exec privledges to the drive and file.. has anyone else had this problem??

---

### Post by pizmal on 2004-12-18
Work around. I got the installer to run by copying the first cd to a tmp dir and running it form there as root in a termial.  Give that a try.  They it just asked for the other cds.

--Pizmal

---

### Post by Ste on 2004-12-19
[QUOTE=pizmal]Work around. I got the installer to run by copying the first cd to a tmp dir and running it form there as root in a termial.  Give that a try.  They it just asked for the other cds.

--Pizmal[/QUOTE]
 Copy the installer to the hard disk and try it that way.

---

### Post by darkoptix on 2004-12-21
[QUOTE=nastynate]howdy all .. . i just installed ubuntu 4.10 and aside from apt not working everything seems ok (updates work via the gui frontend ..  no idea how to fix apt : /  )  but i get a permission denied error when i try to run the UT linux installer as user or root.. i double checked and i know i have exec privledges to the drive and file.. has anyone else had this problem??[/QUOTE]
 type something like:
sudo sh linux-installer.sh
(while in the cdrom dir.)

---

### Post by lameaim on 2004-12-22
[QUOTE=nastynate]howdy all .. . i just installed ubuntu 4.10 and aside from apt not working everything seems ok (updates work via the gui frontend ..  no idea how to fix apt : /  )  but i get a permission denied error when i try to run the UT linux installer as user or root.. i double checked and i know i have exec privledges to the drive and file.. has anyone else had this problem??[/QUOTE]
Check your CD's fstab entry; it has to have "exec" (or defaults) after "user" in the <options> column.

---

### Post by spikeb on 2004-12-22
You need to copy the installer from the cdrom to your hard drive. That's not optional, and a required part of the installation. Otherwise, you cannot change cds.

---

### Post by lameaim on 2004-12-22
[QUOTE=spikeb]You need to copy the installer from the cdrom to your hard drive. That's not optional, and a required part of the installation. Otherwise, you cannot change cds.[/QUOTE]
Sure you can, as long as your not in /cdrom or whatever. eg.:

sh /cdrom/linux-installer.sh

works and you can change cds, but

cd /cdrom && sh linux-installer.sh

wont let you unmount.

---

### Post by ubuntu.daemon on 2004-12-23
[QUOTE=lameaim]Sure you can, as long as your not in /cdrom or whatever. eg.:

sh /cdrom/linux-installer.sh

works and you can change cds, but

cd /cdrom && sh linux-installer.sh

wont let you unmount.[/QUOTE]

I have had better luck with using the 
DVD version of the install, otherwise if u have a cd burner that will usually let u unmoount if u run the discs thru there.   I am now having probs loading it as such:
redxiii@xavier:~ $ ut2004
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

History:

Exiting due to error

I am trying to work past it . . .

---

### Post by Dylanby on 2004-12-24
I just installed the DVD version on my AMD64 system. Bought it today while out Xmas shopping.

First I downloaded & installed the Loki installer for Linux gamers at:
[http://liflg.org/downloadl.php?filename=loki_update-full-1.0.13-x86.run](http://liflg.org/downloadl.php?filename=loki_update-full-1.0.13-x86.run)

Then I used:
$ sh /media/cdrom0/linux-installer.sh

Everything worked fine.

Then I added it to my games menu:
$ nautilus applications:///Games

File -> Create Launcher

Basic Tab ->
Name: UT2004
Command: /home/dylan/ut2004/ut2004
Icon: /home/dylan/ut2004/ut2004.xpm

Game plays as smooth as butter!
Problem: I'm about as good at UT as I am at Linux. 
 ;)

---

### Post by nastynate on 2004-12-27
thanks everyone
but the REAL solution is to go under the computer menu  under removable media and disable the automounting option... installed no prob  :) 
my nvidia drivers are installed and working fine...  but now for some odd reason the game will crash randomly.. sometimes it works ok and sometimes it locks my system...  i cant get any term output since my whole system is deadlocked and i have to poweroff to get out of it.. very wierd

i do have to say that ubuntu does indeed kick ass...  i have been using many different RH based distros for many years... as of now i have suse running onmy laptop and ubuntu on  the desktop... was never a big fan of debian but this istrohas made me 'see the light'  :)  looks like its about time to format the laptop... 

if anyone can point me in the right direction for UT2004 linux troubleshooting id appreciate it th0

---

### Post by mrpro on 2005-02-22
*bump* getting the same error as ubuntu.daemon :( anyone got a solution?

Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

History:

Exiting due to error

running warty and apted the ati drivers..

---

### Post by jdodson on 2005-02-22
[QUOTE=lameaim]Sure you can, as long as your not in /cdrom or whatever. eg.:

sh /cdrom/linux-installer.sh

works and you can change cds, but

cd /cdrom && sh linux-installer.sh

wont let you unmount.[/QUOTE]

yeah.  that is what i did and it worked fine.

---

### Post by mrpro on 2005-02-23
It worked after running fglrxconfig and choosing yes to external apg :)

---

### Post by neighborlee on 2005-02-23
[QUOTE=Dylanby]I just installed the DVD version on my AMD64 system. Bought it today while out Xmas shopping.

First I downloaded & installed the Loki installer for Linux gamers at:
[http://liflg.org/downloadl.php?filename=loki_update-full-1.0.13-x86.run](http://liflg.org/downloadl.php?filename=loki_update-full-1.0.13-x86.run)

Then I used:
$ sh /media/cdrom0/linux-installer.sh

Everything worked fine.

Then I added it to my games menu:
$ nautilus applications:///Games

File -> Create Launcher

Basic Tab ->
Name: UT2004
Command: /home/dylan/ut2004/ut2004
Icon: /home/dylan/ut2004/ut2004.xpm

Game plays as smooth as butter!
Problem: I'm about as good at UT as I am at Linux. 
 ;)[/QUOTE]
----------
sigh...there really should be a README somewhere saying that one MUST first download the loki installer..that or better yet I wonder why they just dont include the dain installer on the CD ?LOL

way better than that ugly ncursed garbage ;-))

THX bigtime for tip though.I was getting SO tired of having to deal with the ncursed GUI  and wondering why loki wasn't loading :(

thx
nl

---

### Post by simonkitch on 2005-06-04
[QUOTE=nastynate]thanks everyone
but the REAL solution is to go under the computer menu  under removable media and disable the automounting option... installed no prob  :) 
my nvidia drivers are installed and working fine...  but now for some odd reason the game will crash randomly.. sometimes it works ok and sometimes it locks my system...  i cant get any term output since my whole system is deadlocked and i have to poweroff to get out of it.. very wierd

i do have to say that ubuntu does indeed kick ass...  i have been using many different RH based distros for many years... as of now i have suse running onmy laptop and ubuntu on  the desktop... was never a big fan of debian but this istrohas made me 'see the light'  :)  looks like its about time to format the laptop... 

if anyone can point me in the right direction for UT2004 linux troubleshooting id appreciate it th0[/QUOTE]
 This is what worked for me, no need to disable automount or install loki installer. Just put the Dvd in the drive. Open a terminal window, type sh /media/cdrom0/linux-installer.sh an bingo...
Thanks guys.

---

### Post by a667bx2838 on 2007-05-15
> **pizmal said:**
> Work around. I got the installer to run by copying the first cd to a tmp dir and running it form there as root in a termial.  Give that a try.  They it just asked for the other cds.

--Pizmal


[Eminem music food science plants Tsunami](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

