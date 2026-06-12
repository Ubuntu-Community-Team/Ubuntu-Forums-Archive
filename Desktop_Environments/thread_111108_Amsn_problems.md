---
title: "Amsn problems"
date: 2006-01-01
forum: Desktop Environments
---

### Post by tellnes on 2006-01-01
Hey,

Just downloaded and installed the new amsn client, 0.95, used the linux installer and autopackage, but still get same error message when i try to launch it; "you cant load TkCximage.." checked faq on msn, tk and tcl is needed but i have booth the newsest of thoose versions.

Someone else experienced this problem and know a howto on it?

//tellnes

---

### Post by Lord Illidan on 2006-01-01
Er, try and get the Ubuntu .deb? I think it should work.

---

### Post by JamesNorris on 2006-01-01
Did you install the tcl/tk development libraries?

I always install aMSN from source, and TkCximage is compiled during the installation, so I'm not sure what could be the problem here.

---

### Post by tellnes on 2006-01-01
[QUOTE=JamesNorris]Did you install the tcl/tk development libraries?

I always install aMSN from source, and TkCximage is compiled during the installation, so I'm not sure what could be the problem here.[/QUOTE]

:( Yea, installed libs and devs for tcl/tk..still same message...damm, new amsn looked so cool too..
Am i the only one who has gotten problems with installing new amsn??
My ubuntu is pretty "default" havent done any wierd things to it..
Can i go into the "amsn" lauch script and edit some paths so it can find the libs it needs? ahh..i get fedora flashbacks now..

---

### Post by JamesNorris on 2006-01-01
I would use either the .deb file or the source file. There is no difference between the debian .deb and the ubuntu one, aside from the default skin, and the debian one is more up-to-date. I would dpkg -i the debian one and see what errors it gives you.

Or, install from source, the configure will tell you what you're missing.

---

### Post by niartv on 2006-01-03
When I try to use the dep package to install I get errors....

> 
ubuntu@ubuntu:/tmp$ sudo dpkg -i amsn_0.95-1.deb
(Reading database ... 57462 files and directories currently installed.)
Preparing to replace amsn 0.95-1 (using amsn_0.95-1.deb) ...
Unpacking replacement amsn ...
dpkg: dependency problems prevent configuration of amsn:
 amsn depends on tcltls; however:
  Package tcltls is not installed.
 amsn depends on libstdc++6 (>= 4.0.1-9); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
dpkg: error processing amsn (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amsn



and

> 
ubuntu@ubuntu:/tmp$ sudo apt-get  tcltls
E: Invalid operation tcltls


what do I have to install to be able to install amsn deb package?

Shiro Niart

---

### Post by syklitengutt on 2006-01-03
sudo apt-get install tcltls

---

### Post by NoWhereMan on 2006-01-03
Seems that the just released ubuntu package was in fact an old cvs; try to download it again ;)

---

### Post by bunced on 2006-01-03
[http://www.ubuntuforums.org/showthread.php?t=75276](http://www.ubuntuforums.org/showthread.php?t=75276) gives instructions for installing aMSN

---

### Post by niartv on 2006-01-03
Clean Install :-)

[http://prdownloads.sourceforge.net/amsn/amsn_0.95-2.ubuntu.deb](http://prdownloads.sourceforge.net/amsn/amsn_0.95-2.ubuntu.deb)

---

