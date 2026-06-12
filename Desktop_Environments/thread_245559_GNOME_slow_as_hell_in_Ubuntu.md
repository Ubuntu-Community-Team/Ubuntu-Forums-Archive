---
title: "GNOME slow as hell in Ubuntu"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Firyar on 2006-08-28
Hi everyone,

at the moment i run Unbuntu 6.06 on my laptop. But there is a very big annoyance i expected since i installed it.

GNOME on this machine is slow as hell. Not only the start of GDM and then finally GNOME, the whole thing seems to be slow and very often i get message in the taskbar "starting application..." and i have to wait. This should not happen on a 1,7 GHZ Pentium mobile with 512 MB and never happened with the Fedora (Core 5) installation which was installed on this machine before. To verify this problem also on other machines, i installed it on the Pentium 4 3Ghz HT machine with 1 GB, and even there i have the problems and encounters mentioned above, but it was a little bit faster. I also tried to use preload and prelink to enhance the speed of these application, but it did not achieve the appropriate effect. 

Am i just spoiled from Fedora and perhaps applied patches which are not in the "official" GNOME release? Or is it a GLIBC problem? I noticed that the output of "/lib/libc.so.6" differs from the output from a Fedora or a Gentoo machine (for example). Has anyone a clue for me? Anyone a solution? I already read the GNOME speed analysis but i think most of the enhancements mentioned there are already implemented (though the bugtracker says they are). I want to use Ubuntu at the laptop, among other things because i am "grown up" with Debian and want to use my knowledge about the distribution for my Ubuntu installations. But i can not use it with a GNOME disaster like this.

Hope anyone can help.

---

### Post by WalmartSniperLX on 2006-08-28
Well im not a pro at this but i know what you mean. I had gentoo and the live cd was as fast as ubuntu. But Ubuntu is FRESHLY NEW and compliles for you. It also has a lot in it that gentoo and/or other distros dont. Like i said i dont really know much about explaining linux. I just got into if from win about a month ago. But from my experience it seems ubuntu has more to offer for an average user and is rebuilt from the ground up every time a new release is released, while gentoo and other distros are just updated from an old original build.

You could try Kubuntu. Its slower at opening by a tad since its kde but for me the desktop point/click navigation seemed faster at opening windows and stuff

---

### Post by acojlo on 2006-08-28
Check the operating frequency of your cpu. To do so add the cpu-freq applet to gnome bar or just "cat" /sys/ ... file.

---

### Post by WalmartSniperLX on 2006-08-28
Honestly ur not the only person to say gnome is slow in ubuntu. I would like to know more and what is causing it to be 'slow':D

---

### Post by Firyar on 2006-08-28
> **acojlo said:**
> Check the operating frequency of your cpu. To do so add the cpu-freq applet to gnome bar or just "cat" /sys/ ... file.

I first thought about this, too. But the frequency is on max. I also disabled the laptop-detect scripts. Even if it would not have been to max, it would not explain the "slowliness" on the P4 workstation.

---

### Post by Firyar on 2006-08-28
> **WalmartSniperLX said:**
> Honestly ur not the only person to say gnome is slow in ubuntu. I would like to know more and what is causing it to be 'slow':D

Me too, believe me. I thought 'bout compiling GNOME for myself, i did it on other machines and used to do it on my Debian machines in the past. If it is still so slow when it is self-compiled, it must be something more deeper inside.

---

### Post by aysiu on 2006-08-28
> **WalmartSniperLX said:**
> Honestly ur not the only person to say gnome is slow in ubuntu. I would like to know more and what is causing it to be 'slow':D
I'm not sure if this is related, but I used to use the default Kubuntu package for KDE (*kubuntu-desktop*). Recently, though, I tried out using *kde-core* instead, and it's been a *lot* faster than *kubuntu-desktop*. Even my GTK apps load up faster in KDE now.

---

### Post by DC@DR on 2006-08-28
That's kinda weird, in my laptop, which is Dell Latitude D600, Pentium M 1.6 GHz, 1GB RAM, GNOME runs smoothly like a charm...Just wonder what cause the "slow" problem you guys encounter..:-?

---

### Post by Perfect Storm on 2006-08-28
> **DC@DR said:**
> That's kinda weird, in my laptop, which is Dell Latitude D600, Pentium M 1.6 GHz, 1GB RAM, GNOME runs smoothly like a charm...Just wonder what cause the "slow" problem you guys encounter..:-?

Same here. Must be something else then.

---

### Post by orb9220 on 2006-08-28
Well ever issue I have seen on this complaint is if you run top and xorg is at the top then it is video drivers not installed or configured correctlly.

Could be wrong just what I remember reading here in the forums.

---

### Post by sque on 2006-08-28
I also think that some things are slow on ubuntu-gnome. xchat is slow on updating the window (when resized, or minimized/maximized) and there is always some jerking. 

The wierd is I have a desktop pc (Athlon XP 2.2 and a laptop Pentim M 1.7) and the laptop works smoothlier than the desktop. I don't know where is the problem but I think it is somewhere among the libraries related to font rendering (pango-mango-cairo whatever-I-am-not-an-expert).

---

### Post by peabody on 2006-08-28
I suspect video drivers as well.  How quickly do things on the screen draw?

---

### Post by Firyar on 2006-08-28
> **peabody said:**
> I suspect video drivers as well.  How quickly do things on the screen draw?

Nope. The video drivers are OK. When i use metacity with pypanel, everything works fine. Frame rates are more than OK. Same with fluxbox or any other WM.

I tested it on the laptop and on the local workstation, one has a Nvidia card, the other on an ATI card. The X.Org settings are exactly the same as i would use them on Fedora or Gentoo!

---

### Post by Cubiq on 2006-08-28
have you experienced this slowness with other distros as well?

---

### Post by Firyar on 2006-08-28
> **Cubiq said:**
> have you experienced this slowness with other distros as well?

I have only tested Ubuntu, Gentoo and Fedora. And only Ubuntu has this "slowliness".

---

### Post by Cubiq on 2006-08-28
I have a Pentium 4 3.4Ghz HT with 1GB and Nvidia 6600 GPU. I must admit that on Arch Linux gnome is way faster than on ubuntu but it is definitely usable on ubuntu as well.

I tried to compile a custom kernel on ubuntu based on 2.6.17 branch and the speed enhancement is noticeable. The problem is that if I custom build the kernel I have to compile by myself many drivers and modules as well and it's too much work for me (semi-newbie) ;)

Probably ubuntu just lack of optimization in favor of a wide hardware compatibility.

---

### Post by dentaku65 on 2006-08-28
see this post, maybe it helps...

[http://ubuntuforums.org/showpost.php?p=1432930&postcount=16](http://ubuntuforums.org/showpost.php?p=1432930&postcount=16)

---

### Post by Cubiq on 2006-08-29
Yesterday I finally got the chance to install xgl+compiz... don't ask me why but gnome seems much more responsive now. Give it a shot if you can.

---

### Post by Paul133 on 2006-08-29
The Live CD for me (and my friend) were unbelievably slow; I couldn't even install it from the LiveCD or the alternate installer. I ended up having to install the server edition and installing Gnome (ubuntu-desktop) from the commandline.

---

### Post by akvik on 2006-11-11
Hi,

My gnome is slow too, and it think it has to do with the network. Don't know if it has to do with anything, but the network I'm on has a netmask 255.255.0.0, and when I'm not connecting to it, I think it takes a while to go through the possible network addresses. Not sure about this, though. If I turn the network interface off, it's fast again.

Does this work for you others as well?

---

### Post by tater_3001 on 2006-11-11
I run a PIII with 512 RAM and it worked fine for me until it crashed;)  i think im gunna try and install xfce...

---

### Post by d3v1ant_0n3 on 2006-11-11
I've not tried another Gnome based distro, but Ubuntu seems mighty snappy to me in comparison to XP on a faster machine. I get a small wait between starting certain apps (Firefox and OO mostly), but only a couple of seconds. Boot is about 90 seconds or so including the time it takes me to put in my password.

---

### Post by tater_3001 on 2006-11-11
ya.. i just installed xfce and it works fine and is pretty fast..8)

---

