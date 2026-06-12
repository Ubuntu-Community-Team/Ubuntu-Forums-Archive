---
title: "Epson C1900 problem"
date: 2005-12-26
forum: General Help
---

### Post by zluka on 2005-12-26
hi all..

newbie, sorry if this looks silly..

i have an epson c1900 at work, directly connected to a router. no problems about ipp, for i can print using the hpijs or the lj4dith driver, but no colors #-o 

does anyone have experience about this? i've read something about the ghostscript version problem, but i don't know if that's the solution..

as i've stated, i can print without problems (and without color) using different drivers, but the "recommended" and "suggested" eplaser driver won't even bother the printer.

thanx

---

### Post by Sef on 2005-12-26
Have you printed a test page with color?   

If it is unsuccessful then I would suspect the problem lies with printer hardware.

If it is successful, then I would suspect the problem lies with driver.

---

### Post by zluka on 2005-12-27
the thing is, i have 3 network (laser) printers at work, c1900 is the only one that's supported by linux (i didn't think that i would have linux at work ;), so didn't bother to check compatibility when i bought them)

and it was used by different users at different times (by direct connection or as a shared printer) and it works fine (when my winblows agrees to boot, i can print any page without problem)

so the printer is tested and good, it's a driver problem indeed :(

actually i finally decided to get rid of winblows (at least on my box, not so bold yet to touch the servers ;)) and i have 3 problems

1. that printer issue
2. games...
3. remote control via VNC (but that's not so hard, i'm just a little lasy about it)

---

### Post by zluka on 2005-12-28
isn't there anyone who fought his way out of something like this?

---

### Post by bogl on 2006-01-04
Hi,

Have you tried using the driver from

[http://www.avasys.jp/english/linux_e/dl_laser.html](http://www.avasys.jp/english/linux_e/dl_laser.html)

and followed my howto

[http://ubuntuforums.org/showthread.php?t=105590&highlight=epson+c1100n](http://ubuntuforums.org/showthread.php?t=105590&highlight=epson+c1100n)

adapted as appropriate?

May solve it, you never know...

bogl

---

### Post by zluka on 2006-01-11
thanx for the reply, but without any success..

for one, that's what can be achieved from linuxprinting.org..

Download for AcuLaser C1900 for Fedora Core 3:
ghostscript-7.07-33ep3.2.0.i386.rpm (rpm package)
or  ghostscript-7.07-33ep3.2.0.src.rpm (source)

Download for AcuLaser C1900 for Red Hat 9:
the same as above, and eplaser-cups-ppd-3.1.6.tgz

downloading the cups driver (and there's no make or configure, just copying) just adds a "foomatic + alc1900" option to my driver selections, which has the same effect as the "recommended eplaser driver", which is nothing...

i want to use that printer, come on guys (and ladies ;))

is anybody out there?..

---

