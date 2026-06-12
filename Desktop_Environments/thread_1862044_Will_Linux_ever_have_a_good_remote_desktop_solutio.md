---
title: "Will Linux ever have a good remote desktop solution?"
date: 2011-10-16
forum: Desktop Environments
---

### Post by r.darwish on 2011-10-16
The whole subject of desktop remote control is very frustrating in Linux, and it seems that it's getting even worse in every new version.
I want the ability to control my currently logged on session from a remote location. There are several programs that claim to provide this ability, but each seems worse then the other.

I tried Vino at start which is pretty easy to configure, but as described [in this bug report]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/772304"), it simply does not work. This bug report was opened over a year and a half ago and the bug was not yet fixed. 
Vino is shipped with the default installation of Ubuntu (and every other Gnome-based distribution). I really don't understand why Ubuntu developers keep offering a feature that is installed by default which stopped working over a year and a half ago. This makes Ubuntu look very non-professional.

Realizing that Vino won't work I switched to x11vnc. Ignoring the fact that there's no GUI way to configure x11vnc I launched it and it seemed to work on my 10.04. However, the performance are terrible comparing to Windows' remote desktop feature, and I'm speaking about performance over LAN, not even over the Internet.

I was kind of happy with this solution in my 10.04 LTS, but when I switched to 11.10 I saw the the classic Gnome desktop is not shipped anymore. Trying x11vnc in composite based desktops like Gnome shell or Unity is even worse then its bad performance in the classic gnome interface.
Switching keyboard layouts using keyboard shortcuts doesn't seem to work either.

Remote desktop feature was implemented in Windows 2000. How is it possible that at the end of 2011 there's still not good and integrated solution for controlling your desktop from a remote location?
Remote desktop is maybe something that the most beginner user won't require, but I really don't think it's such an exotic feature that only extreme power users would require.

Is there any way to make x11vnc perform better, or is there any better solution which I'm now aware of?
I heard about NX, but I want to control my current desktop session, not create a new one.

---

### Post by Lars Noodén on 2011-10-16
You mention that you tried several programs.  Besides Vino, which ones did you try and how did they fail to measure up?  When I last tried krfb/krdc it seemed to work ok.

---

### Post by FLeiXiuS on 2011-10-16
VNC is a horrible solution, look at NX.

---

### Post by Lars Noodén on 2011-10-16
> **FLeiXiuS said:**
> ... look at NX.

There does not seem to be a package for [FreeNX](https://help.ubuntu.com/community/FreeNX) in the Ubuntu repository. :(

---

### Post by r.darwish on 2011-10-17
> **Lars Noodén said:**
> You mention that you tried several programs.  Besides Vino, which ones did you try and how did they fail to measure up?  When I last tried krfb/krdc it seemed to work ok.
krfb is heavily depends on KDE. I rather not install 200 MB of new libraries just for another VNC server

> **FLeiXiuS said:**
> VNC is a horrible solution, look at NX.
Can NX show me my currently logged on session or can it just open new sessions?
If it can, doesn't it do that by simply relaying VNC over its own protocol?

---

### Post by nergaldicuthah on 2011-10-17
We're currently having a like-minded conversation on this subject

[http://ubuntuforums.org/showthread.php?t=1860295](http://ubuntuforums.org/showthread.php?t=1860295)

maybe a moderator can merge the two and all of us work together?

---

### Post by r.darwish on 2011-10-18
> **nergaldicuthah said:**
> We're currently having a like-minded conversation on this subject

[http://ubuntuforums.org/showthread.php?t=1860295](http://ubuntuforums.org/showthread.php?t=1860295)

maybe a moderator can merge the two and all of us work together?
Your conversation is about x11vnc specifically, mine is about remote desktop in general :)

---

### Post by Karlchen on 2011-10-18
My RDP recommendation will be **[Remmina]("https://launchpad.net/%7Ellyzs/+archive/ppa")**, use it on Lucid Lynx 32-bit and really like it and more important, use it every day.

Karl

---

### Post by dradzanowski on 2012-12-28
Team View is the most superior I've found. They have direct Linux support, provide you the deb file (at least for me on Ubuntu distro) as well as most other distros. Great response, great quality. I use it on my home linux computer to control the Windows computer I have running my TV. It's a different kind of remote control!

---

### Post by overdrank on 2012-12-28
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

