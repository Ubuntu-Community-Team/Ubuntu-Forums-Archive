---
title: "Heretic II"
date: 2013-09-11
forum: Gaming &amp; Leisure
---

### Post by windowsfree on 2013-09-11
I found an old CD of Heretic II for Linux that I want to run on my LM 13 distro.  The directions show to go to the directory and run sh install.sh but this distro does not recognize that command.  Can anyone assist with this?   Thank you.

check out the requirements listed in the readme file:
[COLOR=#37404E][FONT=lucida grande]inux kernel version 2.2.x[/FONT][/COLOR]
[COLOR=#37404E][FONT=lucida grande]Pentium 166 MHz with 3D accelerator card, [/FONT][/COLOR]
[COLOR=#37404E][FONT=lucida grande]or 233 MHz for software rendering[/FONT][/COLOR]
[COLOR=#37404E][FONT=lucida grande]32 MB RAM required (64 MB recommended)[/FONT][/COLOR]
[COLOR=#37404E][FONT=lucida grande]4x CD-ROM drive (600 KB/sec sustained transfer rate)[/FONT][/COLOR]
[COLOR=#37404E][FONT=lucida grande]Video card capable of 800x600 resolution[/FONT][/COLOR]
[COLOR=#37404E][FONT=lucida grande]XFree86 version 3.3.x, at 16 bpp depth[/FONT][/COLOR][COLOR=#37404E][FONT=lucida grande]
OSS compatible sound card
Hard disk drive with at least 260 MB of disk space

This product is not intended for use with any version 
of the Windows operating system.[/FONT][/COLOR]

---

### Post by oldrocker99 on 2013-09-11
Copy all the files on the CD to a directory on your desktop. CD to that directory and type

chmod +x install.sh

And try running it again: sudo sh install.sh (you don't need 'run')

---

### Post by windowsfree on 2013-09-11
thank you, I will attempt that and advise here.

---

### Post by MikeCyber on 2013-09-12
only use sudo when needed. Also I don't think that you need to copy the cd content.
cd to the directory and do: 
cd /m*/usern*/media (or wherever)
./install.sh

---

### Post by windowsfree on 2013-09-12
oldrocker99,

I tried your steps and received same error message, I am going to try MikeCyber's suggestion later and will post the results.   thank you both.

---

### Post by windowsfree on 2013-09-20
Still not able to get this to run.....thanks.   any other suggestions?

---

### Post by DarkAmbient on 2013-09-20
If the content of install.sh isn't to large, could you post it? And tell me the error-output from executing install.sh in a terminal

---

### Post by mateo14 on 2013-09-21
[http://liflg.org/?catid=7&gameid=94](http://liflg.org/?catid=7&gameid=94)

---

