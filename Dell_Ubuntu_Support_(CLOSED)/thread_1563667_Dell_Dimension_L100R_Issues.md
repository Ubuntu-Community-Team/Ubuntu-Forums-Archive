---
title: "Dell Dimension L100R Issues"
date: 2010-08-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TechnoDork on 2010-08-29
Hello everyone,

We had an old computer rescued at work by Lubuntu so I decided to install it on my Old Dell. 

Pentium 3 1 ghz
133 Mhz FSB
384 MB RAM
ATI Rage 128 Graphics Card
LG CD-RW CED8080B
WDC 13 GB HDD
Intel 810E Chipset
Lubuntu 10.0.4

First of all, I get this error if I boot with any CD in the drive (common for LG drives from what I can find online):

GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

Now it moves past that and boots, but it almost guarantees that the computer will freeze. A hard freeze too, keyboard goes completely inoperable too. 

However, It doesn't seem to be just the CD Drive. See I'm an x-files Nerd and I've recently been watching some on my PC (AVI format) and decided to try it on my Lubuntu machine. Well they open okay but I've yet to get through an episode without a freeze. I don't know if this is linked to the GLib warning or maybe a problem with my graphics card.

Finally, I get an XML error on bootup everytime, not sure if it is causing any problems or not, but i figured while I'm at it, I might as well post it. Hopefully I will remember to write the exact error down next time I see it so I can be more specific (something about a file expecting '<').

I mainly want my system to stop freezing :( so any help would be greatly appreciated!!

Thanks!

---

### Post by mörgæs on 2010-08-29
Hi, welcome to the forum.

The error message is not specific to one particular error, so it is a difficult problem to solve.

There is a long thread here describing various findings: 
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

Some people claim that it is related to the ext4 file system. A good experiment could be to reinstall Lubuntu with ext3. I can not guarantee that it works, though.

If you do, remember to have wired internet access while installing.

---

