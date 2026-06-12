---
title: "Debian ISO files"
date: 2007-11-03
forum: Debian
---

### Post by GZBurtchell on 2007-11-03
I’ve been really wanting to try Debian, but could someone tell me what’s up with all the ISO files? Over 20 ISO files and I’m saying to myself “Yikes! What am I getting myself into here?”. Which ISO file is what? I’ve searched and I can’t seem to find a description or just a simple explanation.

---

### Post by mindtrick on 2007-11-03
The first CD is enough for base + Desktop Environment. Normal first CD has only Gnome and there are KDE and XFCE first cds also available.

---

### Post by GZBurtchell on 2007-11-03
> **mindtrick said:**
> The first CD is enough for base + Desktop Environment. Normal first CD has only Gnome and there are KDE and XFCE first cds also available.


Well, yeah, I recognize the KDE and XFCE versions, and naturally I assumed the first cd image would be the base install with Gnome. But what are the other 20 ISO image files for?

---

### Post by mindtrick on 2007-11-03
Complete set of packages, you know you see thousands of packages available when you open Synaptic, those CDs contain all of them.

---

### Post by kerry_s on 2007-11-03
the xfce4 is the best for speed->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

remember burn at 4x as a image for best results. type> installgui < if you want the fancy installer.

---

### Post by GZBurtchell on 2007-11-03
> **mindtrick said:**
> Complete set of packages, you know you see thousands of packages available when you open Synaptic, those CDs contain all of them.


Ahhh. Sort of a 'do it yourself'. I can see one advantage of being able to install what I want/need at my leisure from a cd rather than through synaptic/internet. Though there doesn't seem to be any description available for what packages are included in the ISO image files. I'm glad I set aside a 60gb partition for Debian. Looks like it's going to be fun.:-)

---

### Post by kerry_s on 2007-11-03
> **GZBurtchell said:**
> Ahhh. Sort of a 'do it yourself'. I can see one advantage of being able to install what I want/need at my leisure from a cd rather than through synaptic/internet. Though there doesn't seem to be any description available for what packages are included in the ISO image files. I'm glad I set aside a 60gb partition for Debian. Looks like it's going to be fun.:-)

the fun comes when you start learning all the things you can do with debian. i like using the base install and building up from there, it's just amazing how you can change it to fit any way you want it to be and totally make it into your own thing.
i like to be different, mine->

---

### Post by maybeway36 on 2007-11-03
Use the netinst image if you want a one-CD installation and have Internet.
My question is, can the KDE CD #1 completely replace the regular CD#1? I've always wondered this.

---

### Post by GZBurtchell on 2007-11-03
> **kerry_s said:**
> the fun comes when you start learning all the things you can do with debian. i like using the base install and building up from there, it's just amazing how you can change it to fit any way you want it to be and totally make it into your own thing.
i like to be different, mine->

That's why I wanted to try Debian, something I can start out with in a basic way and can build on it my way, and take it on at my own pace. I've been using Ubuntu since late July and while there's some things I like about it, it just isn't the one for me. The only way to describe it is like it's become the Bart to my Homer and too many times I've wanted to do a Homer on it: "Why You Little!.....Ackkkk! Ackkkk! Ackkkk!". I've been trying other distros recently, OpenSuse, Fedora, Mandriva, but none were just right. Though I rather like Mandriva.

Any word on when Lenny stable will be out?

---

### Post by kerry_s on 2007-11-03
lenny, not for a long while. to get lenny you use expert mode, that's what i used on this install. you can just install etch and add the lenny repo, which is much easier. i only jumped straight to lenny for the heck of it, even then i added the etch security repo so i can get the 2.6.18 kernel which works the best for me.

the main thing is you learn how to setup the wm you want to use, when you go custom the setup is up to you.
here's what i do:
i use-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

when it comes to package selection, uncheck them all, that will give you a base install, no gui yet.
log in as root
apt-get install xorg synaptic jwm mc
exit
startx

jwm is what i prefer for window manager, i su and start synaptic to install what ever else i want. i don't use a login manager as i setup my own autologin and startx session.
as long as you install xorg you can put what ever you want after that.
example:
apt-get install xorg gdm synaptic icewm pcmanfm leafpad iceweasel
reboot

that will give you the standard base icewm install with gdm as the login manager, pcmanfm for file manager, leafpad editor, iceweasel browser.

---

### Post by GZBurtchell on 2007-11-06
> **kerry_s said:**
> lenny, not for a long while. to get lenny you use expert mode, that's what i used on this install. you can just install etch and add the lenny repo, which is much easier. i only jumped straight to lenny for the heck of it, even then i added the etch security repo so i can get the 2.6.18 kernel which works the best for me.

the main thing is you learn how to setup the wm you want to use, when you go custom the setup is up to you.
here's what i do:
i use-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

when it comes to package selection, uncheck them all, that will give you a base install, no gui yet.
log in as root
apt-get install xorg synaptic jwm mc
exit
startx

jwm is what i prefer for window manager, i su and start synaptic to install what ever else i want. i don't use a login manager as i setup my own autologin and startx session.
as long as you install xorg you can put what ever you want after that.
example:
apt-get install xorg gdm synaptic icewm pcmanfm leafpad iceweasel
reboot

that will give you the standard base icewm install with gdm as the login manager, pcmanfm for file manager, leafpad editor, iceweasel browser.

The Business Card was too basic for me. I messed up a couple of things and couldn't get myself out of it so I wiped it and installed the standard desktop and system. Just for the fun of it I decided to try the XFCE. So far so good, but I haven't had any time to check everything out yet. But I did change my distro tag on my profile to Debian.:-)

---

