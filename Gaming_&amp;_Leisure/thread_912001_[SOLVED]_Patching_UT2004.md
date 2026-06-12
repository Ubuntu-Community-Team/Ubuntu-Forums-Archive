---
title: "[SOLVED] Patching UT2004"
date: 2008-09-06
forum: Gaming &amp; Leisure
---

### Post by Linux user 66 on 2008-09-06
I've installed UT2004 on my system and downloaded the *UT2004 Mega Bonus Pack Linux.tar.bz2* file. How do I apply the patch?

---

### Post by wishyjr on 2008-09-06
try this thread:

[http://ubuntuforums.org/showthread.php?t=892646](http://ubuntuforums.org/showthread.php?t=892646)

There should be quite a few threads on this if memory serves me well.

---

### Post by Linux user 66 on 2008-09-08
> **wishyjr said:**
> try this thread:

[http://ubuntuforums.org/showthread.php?t=892646](http://ubuntuforums.org/showthread.php?t=892646)

There should be quite a few threads on this if memory serves me well.

Yeah, I've seen most of them. Still can't make it work properly, though. As a matter of fact, I can't even launch the game itself. There is no ut2004.sh file located in the install directory and the file named ut2004 won't do anything. The game was successfully installed and now I just need to find a way to apply the patch and launch the game.

Any other suggestions would be greatly appreciated :)

---

### Post by Perfect Storm on 2008-09-08
32-bit or 64-bit?

---

### Post by Linux user 66 on 2008-09-08
> **Artificial Intelligence said:**
> 32-bit or 64-bit?

It's Ubuntu Desktop Edition 8.04.1 64-bit and I've installed Unreal Tournament 2004 retail version by using the installer on the original DVD. The readme file claimed that the DVD would recognize whether I was running 64-bit or 32-bit and then install the correct version.

---

### Post by Perfect Storm on 2008-09-08
By installing UT2004 on 64-bit is a bit more tricky;

[http://gaming.gwos.org/doku.php/guides:64bit:ut2004](http://gaming.gwos.org/doku.php/guides:64bit:ut2004)

---

### Post by Linux user 66 on 2008-09-10
> **Artificial Intelligence said:**
> By installing UT2004 on 64-bit is a bit more tricky;

[http://gaming.gwos.org/doku.php/guides:64bit:ut2004](http://gaming.gwos.org/doku.php/guides:64bit:ut2004)

I followed the guide, but some of the steps didn't work. I noticed that the default installation directory is */home/(name)/ut2004*. Should I try reinstalling and change the installation directory to */usr/games* or something?

[Edit] (Don't know why that "devil" smiley appeared. I didn't pick any.)

---

### Post by Perfect Storm on 2008-09-10
If you install it in diffrent path than shown in the guide you have to make sure to make the changes through the guide - also if you install it in your home directory - sudo is not needed.

---

### Post by Linux user 66 on 2008-09-10
> **Artificial Intelligence said:**
> If you install it in diffrent path than shown in the guide you have to make sure to make the changes through the guide - also if you install it in your home directory - sudo is not needed.

I understand, but does the UT2004 installation guide take for granted that the default installation directory is *usr/local/games*? 

For me, the default directory is *home/(user name)*. If I change the installation directory to *usr/local/games* in the setup on the DVD, can I then follow the guide *precisely*?

If not, then what directory should I have the DVD install the game to, in order to follow the guide precisely (without changing the given commands)?

@ Artificial Intelligence

By the way, I really appreciate your patience.

---

### Post by Perfect Storm on 2008-09-10
> If I change the installation directory to usr/local/games in the setup on the DVD, can I then follow the guide precisely?

Yes.

> By the way, I really appreciate your patience. 

My pleasure ^_^

---

### Post by Linux user 66 on 2008-09-16
I'm actually still struggling with this, believe it or not. I discovered (yeah I know, won't get any applause here) that the reason for why the default installation directory was */home/(name)/ut2004* was because of the fact that I launched the Linux installer on the DVD manually and not by using the sudo command in the terminal, which would have given it root access.

When I try to launch the installer by using the terminal, it just won't work. I think it's because I've typed in an incorrect path, but I've run out of ideas as to what the patch for my optical drive really is. The name of my optical drive appears to be *cdrom0*, but maybe it's something else.

I've tried:

sudo sh /media/UT2004_DVD/linux-installer.sh

sudo sh /media/cdrom0/UT2004_DVD/linux-installer.sh

sudo sh /cdrom0/UT2004_DVD/linux-installer.sh

Is there any other path I can try?

---

### Post by Perfect Storm on 2008-09-16
Open the DVD.
Open the Terminal.

You can drag the file path to the terminal.

---

### Post by Linux user 66 on 2008-09-16
> **Artificial Intelligence said:**
> Open the DVD.
Open the Terminal.

You can drag the file path to the terminal.

Beautiful! Got it working now, finally. :)

Thanks a lot for your help!

---

