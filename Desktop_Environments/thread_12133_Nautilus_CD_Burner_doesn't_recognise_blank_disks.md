---
title: "Nautilus CD Burner doesn't recognise blank disks"
date: 2005-01-22
forum: Desktop Environments
---

### Post by lildude on 2005-01-22
Hi there

Here's the situation, Nautilus correctly identifies by CDRW drive, it automatically opens the CD Creator box when I insert a blank CD, it lets me create ISO's, but it won't allow me to burn to the CD, from the CD creator box or from ISO's.  Everytime I try, either as root or a normal user, I get the error 

Please put a rewritable or blank disc, with at least 60 MiB free, into the drive.

The disk in the drive IS a blank 700Mb CD.  

FYI: I'm running Hoary and I am able to burn my ISO's to CD's without any problems from the command line as root or a normal user.  Oh yes, and the drive is an ATAPI cdrom.

Any ideas why it won't recognise the size of my CD's correctly?

---

### Post by valadil on 2005-01-22
I've got a similar problem.  It tells me there's not enough space on the CD.  I tell it to check again and it does and then everything works.  Not too big of a deal, except that other installations of Ubuntu on the same exact hardware have worked flawlessly.

---

### Post by lildude on 2005-01-24
[QUOTE=valadil]I've got a similar problem.  It tells me there's not enough space on the CD.  I tell it to check again and it does and then everything works.  Not too big of a deal, except that other installations of Ubuntu on the same exact hardware have worked flawlessly.[/QUOTE]
 It would be nice if this worked for me.  I can click the "Retry" button until the cows come home and it still doesn't recognise the CD is completely blank.

---

### Post by filip on 2005-02-20
lildude: I had precisely the same problem as you, but i was finally able to solve it:

Start gconf and go to apps->nautilus-cd-burner

I turned burnproof, debug and overburn on, and the problem stopped!

I don't know why....

---

### Post by lildude on 2005-02-26
[QUOTE=filip]lildude: I had precisely the same problem as you, but i was finally able to solve it:

Start gconf and go to apps->nautilus-cd-burner

I turned burnproof, debug and overburn on, and the problem stopped!

I don't know why....[/QUOTE]

Spot on buddy. It works a treat now. Bit odd that you have to enable these to get it working, even if your device doesn't support burnproof or overburn.  But hey ho, it works so one more happy chappy.

---

### Post by Sham on 2005-02-26
[QUOTE=filip]lildude: I had precisely the same problem as you, but i was finally able to solve it:

Start gconf and go to apps->nautilus-cd-burner

I turned burnproof, debug and overburn on, and the problem stopped!

I don't know why....[/QUOTE]

How do you start gconf? Prolly a silly question, but typing gconf in terminal does nothing. According to synaptic, I have gconf2 installed.

Cheers

---

### Post by ceti on 2005-02-26
Hi, Sham.
To run gconf:
Applications --> System Tools --> Configuration Editor

Happy trails...

---

### Post by martijntje on 2005-02-26
Darn it. It doesn't work for me.
It use to work when i had ubuntu installed on my old HD.

---

### Post by ReddoC on 2005-04-06
[QUOTE=martijntje]Darn it. It doesn't work for me.
It use to work when i had ubuntu installed on my old HD.[/QUOTE]


I have installed Hoary last week. Everything has been detected.

TDK CDRW241040X

Everything look to be working until I press the write button and then nautilus ask me
to insert a blank disk.

I tried to change the option in gconf, but nothing happend.

the only thing i saw is a nautilus msg in the terminal that say:


(nautilus-cd-burner:16221): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


That could be the problem ?

ReddoC

---

### Post by lorap on 2005-04-06
hi friend!
why wouldn't you just install the "k3b" or GraveMan or GnomeBaker?
this's the link 
[http://gnomebaker.sourceforge.net/](http://gnomebaker.sourceforge.net/)
this'll probably solve the problem.
k3b's the best one i've ever seen.
have a nice day!
pavel

---

### Post by gnel on 2007-06-11
For those who the published workarounds didn't work maybe can test if the problem is in the permissions of the device file  because that was my problem on a similar bug[1] I had.

[1] [http://bugs.gentoo.org/show_bug.cgi?id=100460#c7](http://bugs.gentoo.org/show_bug.cgi?id=100460#c7)

---

### Post by Tha_Joel on 2007-07-02
Same Problem But Where Can I Download Nautilus????

---

### Post by plantman on 2007-10-21
> **filip said:**
> lildude: I had precisely the same problem as you, but i was finally able to solve it:

Start gconf and go to apps->nautilus-cd-burner

I turned burnproof, debug and overburn on, and the problem stopped!

I don't know why....

I also noticed in gconf that my speed was 0. I set it to 4 and it worked!!!!!!!!!!!:):):):):)

---

