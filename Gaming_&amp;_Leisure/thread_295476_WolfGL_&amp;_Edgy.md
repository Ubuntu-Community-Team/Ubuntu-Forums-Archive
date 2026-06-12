---
title: "WolfGL &amp; Edgy"
date: 2006-11-08
forum: Gaming &amp; Leisure
---

### Post by hikaricore on 2006-11-08
Anyone having luck running wolfgl on edgy?

I've tried a number of different builds and they either end up spitting out this:

> /wolfgl: relocation error: ./wolfgl: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference


or a similar line in refernce to libm.so.6

I have every library I could possibly need installed, and linking libc.so to libc.so.6 (VERY VERY BAD IDEA NEVER DO THIS) didn't do anything but kill the use of every terminal on my system, had to remove it via nautilus lol  good thing my X stayed running. :P

I'm unable to find the source for anything but wolf3d and newwolf, neither of which even come with make scripts. >.<

It could just be my system, I have two boxes with edgy at work a server and a desktop publishing system that I'll try it on tomorrow.  I even dug out my down the original wolfenstein3d disks from a box in my closet that I never open hehe.  I know I could run it in dosemu or find a windows port and wine it, but that kinda defeats the purpose.

Thanks in advance if anyone can point me in the right direction.  And for the 300th time no I don't want to play enemy territory.  :)

---

### Post by hikaricore on 2006-11-08
**Update**  Tested this on two **upgraded** (from dapper) edgy systems at work and got the same error output, one was ubuntu and the other kubuntu.  I ran it on a dapper system I setup real quick from a junk server and it started up.  I didn't have any game files but it still started without error.  So I'm guessing this is either a kernel issue or an issue with updated libraries not playing nicely with a binary compiled using old libraries headers.  So far I still havn't been able to find a source release for WolfGL. :/

--Aaron

---

Tomorrow I will try installing fresh edgy from a cd on the junk server and see if the issue still exists, just to test the upgrade vs. new install possibility.  (maybe upgrade doesn't build links correctly enough for a badly build binary?  just a thought)

---

### Post by hikaricore on 2006-11-12
Eh, I've still got nothing.  Can't compile/run any of the linux ports.  Guess I'll just find a nice winport and run it in wine.  :P  Was worth a shot hehe.

---

### Post by DaneDog on 2007-01-16
I know this is an old post... but i found a walkthrough for this if anyone searches wolfgl this is the only return... maybe this might help someone :)

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wolfenstein](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wolfenstein)

---

### Post by hikaricore on 2007-01-16
> **DaneDog said:**
> I know this is an old post... but i found a walkthrough for this if anyone searches wolfgl this is the only return... maybe this might help someone :)

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wolfenstein](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wolfenstein)

Aye thanks for posting this :)

I actually forgot this post, but in the mean time I found working debian packages for Wolf3D here:

[http://home.icequake.net/~nemesis/debian/binary/](http://home.icequake.net/~nemesis/debian/binary/)

You can add this to your sources.list file if needed as:
> 
## nemesis : wolf3d ##
deb [http://home.icequake.net/~nemesis/debian](http://home.icequake.net/~nemesis/debian) binary/
deb [http://home.icequake.net/~nemesis/debian](http://home.icequake.net/~nemesis/debian) warez/
deb-src [http://home.icequake.net/~nemesis/debian](http://home.icequake.net/~nemesis/debian) source/

---

