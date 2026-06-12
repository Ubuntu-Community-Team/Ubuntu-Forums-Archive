---
title: "Careful with updates!"
date: 2006-09-15
forum: Desktop Environments
---

### Post by kikinovak on 2006-09-15
Hi,

I'm working as a sysadmin in Montpezat/South France. Running a database server (Debian Sarge), and a pack of Ubuntu 6.06 clients connected to that, in a public library. I'll soon have to migrate eleven more towns (town halls, public libraries) around here, following a regional decision.

My choice of Ubuntu was for ease of install, plus the quality of localizations (that's where most distros lag behind). Before that, I've been a die-hard Slackware user, for the sheer quality of that distro (everything was - and still is - just perfect... except many things are missing desktop-wise). 

One plead to the Ubuntu people: please! be! careful! with! what! you! put! into! update! repos! Recently we've had the big mess with the x-server update... now it's the nvidia-kernel-modules that break everything. Continue like that, and people will fly back in the arms of the Microsoft crap (last booted around 2001 here). 

</rant>

---

### Post by Sef on 2006-09-15
The X-server was Ubuntu's mistake.  However, the problem nvidia-kernel-modules is that they are not opensource.  If they were opensource this would not happen.

---

### Post by elettronicha on 2006-09-15
> **kikinovak said:**
> Hi,
One plead to the Ubuntu people: please! be! careful! with! what! you! put! into! update! repos! Recently we've had the big mess with the x-server update... now it's the nvidia-kernel-modules that break everything. Continue like that, and people will fly back in the arms of the Microsoft crap (last booted around 2001 here). 
That is just what I was thinking right now, reading about the recent issues (clear! of today and of august). Probably some packager/developer forgot Dapper is a "STABLE" release and aims to be a "LONG TERM SUPPORT" release, suitable both for desktop and for production servers.

Maybe some package needs a little bit more testing before been released?

---

### Post by elettronicha on 2006-09-15
> **Sef said:**
> The X-server was Ubuntu's mistake.
OK.

> the problem nvidia-kernel-modules is that they are not opensource.  If they were opensource this would not happen.
Do you mean other distros share the same problem? If a package has some issue, just don't release it before has been tested enough, that is my opinion.:)

---

### Post by dietrying on 2006-09-15
I like Ubuntu very well and it's one of the best linux distributions iv'e ever seen BUT:

"One plead to the Ubuntu people: please! be! careful! with! what! you! put! into! update! repos!"

I totaly agree with this......problems with programs from universe or multiverse  may happen (like the thing with f-spot), but beeing not able to start x or get an internet connection after update is not acceptable for a stable release. The little red update button should only appear, when it's SECURE.

greetings, David

---

### Post by linuxNewb on 2006-09-15
It's not just the X-Server thing. I just updated the kernel and restricted modules today through the update manager and now my internet is broken ( see [http://ubuntuforums.org/showthread.php?t=257998](http://ubuntuforums.org/showthread.php?t=257998) ). Since I'm not the one who openned that thread, obviously it's not an issue unique to my system. I figured the X-Server thing was just a one time slip, but after this second system break, I will wait and watch the forums for a few days after updates are released before updating packages.

---

### Post by ATAQ on 2006-09-15
Ya the new updates messed me up again. when I install the nvidia drivers and start x up again its grand, but i have to re do this every boot since that update

---

### Post by wkulecz on 2006-09-15
> **Sef said:**
> The X-server was Ubuntu's mistake.  However, the problem nvidia-kernel-modules is that they are not opensource.  If they were opensource this would not happen.

And if the nv drivers shipped with Ubuntu weren't broken, I'd be using them instead!

Fedora Core 5 had the same performance regression with the X video extensions but the FC5 team quickly folded in the fix as X.org bugzilla lists the issue as fixed, but this hasn't yet found its way into recent (post FC5) Debian based Xorg 7.0 distros I've tried (Ubuntu 6.06 and Knoppix 5.0.1).

I first joined this forum to find a fix, and the fix was "install the nvidia-glx drivers".

Thus the Ubuntians can't dodge the blame for this snafu!

--wally.

---

### Post by wkulecz on 2006-09-15
delete duplicate

---

