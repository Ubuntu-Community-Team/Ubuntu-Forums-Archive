---
title: "Enemy Territory install errors"
date: 2006-11-27
forum: Gaming &amp; Leisure
---

### Post by Extr3me on 2006-11-27
I have been trying to install the linux version of Enemy Territory on my workstation but I am having some problems. I have done this before on my laptop and everything worked OK, but on my workstation it throws some funny error during the unpacking of the archive.

[I][INDENT]sudo ./et-linux-2.60.x86.run 
Password:
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................
./setup.sh: 278: /home/ewan/.setup15307: not found
./setup.sh: 289: /home/ewan/.setup15307: not found[/INDENT][/I]

Above is the output from my terminal.  Even if I unpack the archive to a folder and then run the *setup.sh* file, it still throws an error such as:

[INDENT][I]sudo ./setup.sh
./setup.sh: 278: /home/ewan/.setup15369: not found
./setup.sh: 289: /home/ewan/.setup15369: not found
[/I][/INDENT]

Any suggestions would be welcome, this game is great fun on the office LAN.

---

### Post by briguy on 2006-12-17
I'm having the same trouble.  I'm trying to install it on a 64-bit version, which I'm assuming is part of the problem.  Did you find a solution?

---

### Post by briguy on 2006-12-19
Ok, I got it to work.  What I did was use Automatix2 to install some 32 bit applications, which automatically installed some required 32 bit libraries.  Works like a charm now!

---

### Post by lakersforce on 2007-04-21
I found the solution! Look here: [http://ubuntuforums.org/showthread.php?t=416871](http://ubuntuforums.org/showthread.php?t=416871)

---

