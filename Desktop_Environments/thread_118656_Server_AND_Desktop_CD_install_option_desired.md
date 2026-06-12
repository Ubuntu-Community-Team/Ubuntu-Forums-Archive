---
title: "Server AND Desktop CD install option desired"
date: 2006-01-17
forum: Desktop Environments
---

### Post by xenon2000 on 2006-01-17
Before everyone jumps and says, just do this: [http://www.ubuntuforums.org/showthread.php?t=118189&highlight=server+gui](http://www.ubuntuforums.org/showthread.php?t=118189&highlight=server+gui)

I have seen the above thread and many other ways to either start with Server Ubuntu install and ADD Xwindow desktops to it. And I have seen the options for Desktop Ubuntu install and then adding all the server dev tools and services such as SSH, DHCPD, etc.

Both those work. But would be really nice if there was a 3rd install option:
SERVER + DESKTOP. 

Also having the option of what "desktops" to install would be nice to. Example:
SERVER + Xfce
SERVER + Gnome
SERVER + KDE

I want to be able to do a quick fresh install and end up with all the dev and services that SERVER install gives me AND have an xwindows setup and ready to use by running startx.

Since I already know of the current solutions for my end results, I am not asking for more solutions to the end result. Just a "CD Installer" request. Maybe something that could be worked into the Dapper install CD? Would rock to be able to simply Choose SERVER + Xfce and install.

---

### Post by christhemonkey on 2006-01-17
but would all that fit on one cd?

---

### Post by carlosqueso on 2006-01-17
[QUOTE=xenon2000]Before everyone jumps and says, just do this: [http://www.ubuntuforums.org/showthread.php?t=118189&highlight=server+gui](http://www.ubuntuforums.org/showthread.php?t=118189&highlight=server+gui)

I have seen the above thread and many other ways to either start with Server Ubuntu install and ADD Xwindow desktops to it. And I have seen the options for Desktop Ubuntu install and then adding all the server dev tools and services such as SSH, DHCPD, etc.

Both those work. But would be really nice if there was a 3rd install option:
SERVER + DESKTOP. 

Also having the option of what "desktops" to install would be nice to. Example:
SERVER + Xfce
SERVER + Gnome
SERVER + KDE

I want to be able to do a quick fresh install and end up with all the dev and services that SERVER install gives me AND have an xwindows setup and ready to use by running startx. [/QUOTE]


A server install is simply a minimal install...you actually still have to install all of the server packages to get SSH, etc.  (I know it's misleading....but that's what it is).  If you want a server with GNOME, do a full install of Ubuntu.  If you want a server with KDE, install Kubuntu.  If you want a server with Xfce, you're screwed until we get xubuntu on CD.  Is it a perfect system? No, but I just thought I'd clarify.

---

### Post by xenon2000 on 2006-01-17
[QUOTE=christhemonkey]but would all that fit on one cd?[/QUOTE]

Well, I don't know about if it included other desktops like Xfce or KDE...

But it would definately fit on 1 CD if it contained just the regular SERVER and Gnome desktop that is currently on the 5.10 CD. The only difference is that you would be able to say SERVER + DESKTOP instead of just SERVER or Desktop like it is currently.

Even if I could just say SERVER + DESKTOP and have gnome Ubuntu with all the SERVER stuff from a fresh install, that would be awesome.

Though, if CD space was an issue to add the Xfce desktop to the CD for a SERVER + Xfce option, it chould first check for a network connection and if it can get the files via the internet, then it could activate the option for SERVER + Xfce , etc.

But even with just the CD the way it is now, if they added 1 more option for SERVER + DESKTOP instead of just "server" or "press ENTER to install Desktop" , then that would rock as well.

---

### Post by xenon2000 on 2006-01-17
[QUOTE=carlosqueso]A server install is simply a minimal install...you actually still have to install all of the server packages to get SSH, etc.  (I know it's misleading....but that's what it is).  If you want a server with GNOME, do a full install of Ubuntu.  If you want a server with KDE, install Kubuntu.  If you want a server with Xfce, you're screwed until we get xubuntu on CD.  Is it a perfect system? No, but I just thought I'd clarify.[/QUOTE]

I know that an "Ubuntu server" install is a minimal install, and I am not suggesting that we change that. It's a great option. I have used it.

I am saying that it would be nice if there was a 3rd Option at install for SERVER + DESKTOP (never mind the extra coolest of choosing which Desktop).

Personally I am still a huge fan of the Slackware installer. I get a simple menu to pick what I want. If I want just a server, I pick base linux and the dev packages. If I want the desktop, I add that. etc. And and the 2nd step I have the choice of an unattended install or levels of interaction for each part of the packages. I always do the full unattended though. :)

---

### Post by christhemonkey on 2006-01-17
yeah, like some sort of advanced option?

---

### Post by lamego on 2006-01-17
It is not a very common combination, DESKTOP+SERVER, it maybe nice to you and a few other guys but in my oppinion that is not enough to justify such an option :P.

---

### Post by xenon2000 on 2006-01-17
[QUOTE=lamego]It is not a very common combination, DESKTOP+SERVER, it maybe nice to you and a few other guys but in my oppinion that is not enough to justify such an option :P.[/QUOTE]

Sad comment indeed. Linux is not about what is "common". I guess Slackware's age shows it's wisdom. Very little would have to be done to make the current 5.10 install CD do a SERVER+DESKTOP install.

But to say that it's not common (which I don't agree that a Server with xwindows in uncommon) is a sad reason to to not make an install CD more flexible with little work.

And again, I don't agree without. But that would be another thread on it's own. I just wanted to point out that I think it's a sad opinion to say that a Linux distro should lack flexibility that is easy to obtain just because you think the need isn't high enough.

Even right this minute, there are plenty of popular distros that let you do a server with Xwindows at install. Slackware is the one I have used in this regard for at least the past 6 years. RedHat EL is another. (Which I can't stand RHEL)

Am I truely alone on this desire for Ubuntu? Are all the Ubuntu users strictly divided between "SERVER with no X" and "Desktop with no Server" groups? I highly doubt it. I certainly know this isn't the case with other distros.

Don't get me wrong, there is definately a place for the 3 main setups:
SERVER with no X
Desktop with no Server
SERVER with X

I use all 3 setups. Currently my web server is a 3.2Ghz Server with no X windows. And then I have a router that is only 500Mhz with X. Sounds backwards or unnessary, but I have reasons for both setups.

---

