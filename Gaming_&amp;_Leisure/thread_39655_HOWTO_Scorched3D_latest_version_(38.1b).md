---
title: "HOWTO: Scorched3D latest version (38.1b)"
date: 2005-06-06
forum: Gaming &amp; Leisure
---

### Post by teumima on 2005-06-06
I don't know how many of you have tried Scorched 3D. I highly recommend it.

Make sure you have your 3D acceleration working.

scorched3D is in the repos, however it is not the latest version and since most players have the latest version you won't be able to play with/against most people online. 

So I made this simple HOWTO.

Open terminal

wget [http://switch.dl.sourceforge.net/sourceforge/scorched3d/Scorched3D-38.1-i386.rpm](http://switch.dl.sourceforge.net/sourceforge/scorched3d/Scorched3D-38.1-i386.rpm)

(make sure its all on one line. The forum wont let me put it all on one line)

then once the dowload is complete:

sudo alien Scorched3D-38.1-i386.rpm 

then:

sudo dpkg -i scorched3d_38.1-2_i386.deb

There you go. Now you have the latest version of Scorched 3D. 

NOTE: Some users might get an error during the dpkg process. In that case. Do this:

sudo apt-get install scorched3d

say yes to all dependencies

then sudo apt-get remove scorched3d

and then follow my HOWTO from the top again :)

---

### Post by spiderworm on 2005-08-11
Is there a way to do it for those of us on 64 bit Hoary?

spiderworm

---

### Post by drizek on 2005-08-11
[QUOTE=spiderworm]Is there a way to do it for those of us on 64 bit Hoary?

spiderworm[/QUOTE]
 should be the same way. you just have to use 32bit packages.

---

### Post by charlieg on 2005-08-12
Scorched3D 39 is now out anyway!

---

### Post by spiderworm on 2005-08-15
How do I use 32 bit packages on a 64 bit system?  I tried it btw and it errored out...  Am I supposed to do it through a dchrooted environment, or what?

---

### Post by tareko on 2007-01-10
Hey all!

I note that the same technique worked well for the newest version (at this time), 40.1d

tarek : )

---

