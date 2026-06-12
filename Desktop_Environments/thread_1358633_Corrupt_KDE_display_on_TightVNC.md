---
title: "Corrupt KDE display on TightVNC"
date: 2009-12-18
forum: Desktop Environments
---

### Post by luciphercolors on 2009-12-18
Hi everyone,

Running into a weird problem. I am a Windows guy and use Linux mostly for server-type duties. I recently wiped out a botched OpenSUSE 11.2 in-place upgrade to install Ubuntu Server. I am trying to set up a KDE-based VNC desktop and running into this weird *** glitch:

[img]http://i47.tinypic.com/2sayn0w.png"]http://i47.tinypic.com/2sayn0w.png[/img]

This is on a stock, extremely minimal server install where I manually installed KDE and X and VNC through their respective aptitude meta-packages.

My ubuntu install is currently running inside VMWare Server 1.0.10, however before I set this up I was very briefly running into the exact same thing when I ran Ubuntu Server on the bare hardware (ended up wiping that out and installing US 6.02 LTS as the host OS because I didn't want to hack things just to run VMWare)

I have made sure to install KDE via the instructions at [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE). I installed the "kde" metapackage, along with x-window-system-base and tightvnc.

The screenshot has VNC start with xsession, and I launched KDE by typing startkde at the command prompt in the window. I tried searching these forums but have not had any luck -- my apologies if this is brought up somewhere else :-)

Also- if I want to run Gnome apps, what packages (bare minimum) do I need to have installed?

Finally- I like KDE4 but the UI (font sizes especially) is just too damn big. I don't like Fischer-Price GUIs :-/ ... any suggestions on trimming the fat? That's my biggest complaint over KDE3 (and KDE3/Gnome/MacOSX over Windows)

---

### Post by luciphercolors on 2009-12-18
Sad, nobody? :-(

---

### Post by jdh30 on 2010-03-09
Three years after you posted the problem I can now say that I am still having this VNC corruption problem. Still hasn't been fixed. I just had it with two Debian installs and now I'm having it with my new Kubuntu install. I only moved to Kubuntu because none of the Debian's would run correctly on this Dell PowerEdge T605. I would use Ubuntu instead but the only thing I really want is my e-mail from KMail so I need KDE and Ubuntu ships with Gnome. I tried Ubuntu on my laptop and it didn't work at all there either.
 
I thought perhaps this problem was caused by dodgy ATi drivers so I removed them and reverted to Vesa but the problem was still there. I have found that x11vnc does work but this server has a crappy video card so I only get 1280x1024 and unusably-bad performance.
 
I'm only having these problems (after a week of trying to find any Linux that will work on this 1 year old Dell!) because I accidentally updated my old Debian install to KDE4 only to discover that KDE4 sucks beyond belief. My log files are now full of segfaults and the Debian FAQ's question about reverting to an older distro answers it with "why would anyone ever want to do that?". Wow, thanks.
 
I'm so sick of all of these problems that I'm giving up on Linux after 10 years and moving to Windows. I just wasted a week trying to get this worthless software to start. :-(

---

### Post by krunge on 2010-03-10
Actually the OP was from last December; his/her forums join date is from 2007 though.

---

### Post by RParr on 2010-09-22
I too am experiencing this problem on Ubuntu 10.04.

It is very specific to the KDE 4 desktop accessed via VNC.

That is, if I access the same Ubuntu 10.04 server, using the same kdm or gdm, and the same vncviewer BUT I open an Gnome desktop it display nicely with none of the corruption seen on the KDE 4 desktop.

Further, if I access a different server with Ubuntu 8.04, both the KDE 3.5 and the Gnome desktop look great.

I have searched a lot and have found many with this problem but no answers.

Any help would be greatly appreciated

R.Parr, RHCE, Temporal Arts

---

