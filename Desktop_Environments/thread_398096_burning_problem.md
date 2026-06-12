---
title: "burning problem"
date: 2007-03-31
forum: Desktop Environments
---

### Post by john-d on 2007-03-31
Hi,
I've got a dvd writing problem, every time I try burning a dvd with any program, the dvd comes right back out and I get a error message. Heres the message I get with k3b:
System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-28-386
Devices
-----------------------
MATSHITA UJ-840D 1.00 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; Restricted Overwrite]

Used versions
-----------------------
growisofs: 7.0.1
mkisofs: 2.1-unofficial-iconv

growisofs
-----------------------
:-( unable to pread64(2) primary volume descriptor: Input/output error
    you most likely want to use -Z option.

growisofs command:
-----------------------
/usr/bin/X11/growisofs -M /dev/hdc -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -speed=8 -use-the-force-luke=bufsize:32m -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-john-d/k3bv9Zvpb.tmp -rational-rock -hide-list /tmp/kde-john-d/k3bndWxOa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-john-d/k3boxXFka.tmp -full-iso9660-filenames -iso-level 2 -input-charset iso8859-15 -path-list /tmp/kde-john-d/k3bPUcEMa.tmp

I tried running the growisofs commant in a terminal, but it doesn't work, i tried putting in the -Z command but it doesn't work either and I know it's not a permission problem, and it has worked in the past since i've been using it for three months. Please help me.

---

### Post by PurplePenguin on 2007-03-31
Looks like it might be a bug.  [Here's something to read]("http://k3b.plainblack.com/message-board/unable-to-pread64---dvd-burn").

I don't want to be one of the guys just saying "Google it", but I find that's the best way to figure out weird error messages.  I googled the one part of your error (unable to pread64(2) primary volume descriptor: Input/output error) and [got a bunch of hits]("http://www.google.ca/search?q=unable+to+pread64(2)+primary+volume+descriptor%3A+Input%2Foutput+error") that look like they'll help you.

---

### Post by john-d on 2007-03-31
thanks, but i didn't find anything useful for now,i'll keep serching, but i doubt ill find anything

---

### Post by PurplePenguin on 2007-03-31
Have you tried using any other cd/dvd burning programs?  Just in case it is a bug with k3b (seems like people are only getting this error with k3b), any other program should work fine.

---

### Post by john-d on 2007-04-01
I have tried with a lot of ather programs, but none work

---

