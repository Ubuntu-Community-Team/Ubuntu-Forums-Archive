---
title: "Kaffeine 0.8.1 sound problems with DVB-T"
date: 2006-09-06
forum: Desktop Environments
---

### Post by master_b on 2006-09-06
Just installed Kaffeine 0.8.1 on a new Dapper installation.

Set up DVB-T and scanned for channels and added same.

Problem: - some channels have no sound.

Went to DVB menu/Channels and right-clicked a few channels - seems that those that have Audio PID# sound set to (ac3) work, but not all channels have this default, some have PID# (eng).

Attempted to change a couple from (eng) to (ac3) - some worked, other didn't.

Had no such problems with Kaffeine 0.7.1, nor with Kaffeine 0.8.1 on MythDora and other LiveCD distros.

I'll keep playing with settings, but as long as I get one working broadcast for each channel, that will do for me ( I'm in Sydney, Australia and each Channel has more than one HD/Digital/HD Digital Broadcast).

Anybody else have similar problems?

Bill

---

### Post by dabros on 2006-09-20
Hi,

I have the same problems using Kaffeine 0.7.1 (based on KDE 3.5.2) on Ubuntu Dapper Drake. No sound without choosing ac3. But I couldn't figure it out so far. Did you find any solution to that problem?

dabros

---

### Post by dabros on 2006-09-23
Hi,

I solved the problem simply by installing "libxine-extracodecs". I read something about sound and those binaries in here

[http://www.ubuntuforums.org/showthread.php?t=179138&highlight=xgl+kaffeine](http://www.ubuntuforums.org/showthread.php?t=179138&highlight=xgl+kaffeine)

and tried it. Now Kaffeine works perfectly for me.

Hope that helps.
Dabros

---

