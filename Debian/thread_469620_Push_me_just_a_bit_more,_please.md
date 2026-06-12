---
title: "Push me just a bit more, please"
date: 2007-06-10
forum: Debian
---

### Post by DirtDawg on 2007-06-10
I have an imac g3 (new gen) that has been running Xubuntu Dapper for about a year now. I've recently been trying to get the 3D acceleration to work, with no luck, and finally borked X to the point where I can't even get a terminal up long enough to run, "sudo cp xorg.conf.bak xorg.conf", if you know what I mean.

Since *buntu dropped their PPC support (BOO!), I've been looking at other distros and Debian looks more and more like a good alternative, but I have just a few questions.

1) Is it true Debian is not really any more difficult to install and set up than *buntu? I would consider myself an intermadiate Linux user as I have been using Linux since 2002, but I still rely heavily on tutorials and howto's for many tasks.

2) Should I use Etch or Lenny? I see Etch has plenty of fans, but I wonder about the "staleness" of the packages. That said, they couldn't really be much older than the Dapper packages I was using anyways, is this correct? In addition, is it possible to, for example, install Lenny packages on an Etch install? The equivalent would be impossible on *buntu.

3) I believe, with an internet connection, if I install the "*xcfe-cd-1.iso", this will install the base system plus xcfe, then get everything else from the internet. Am I correct in this assumtion? In other words, will this be the only cd I need?

4) Is there anything else I should know? I'm close to giving Debian the old college try, but I could use just a little push, or perhaps dissuasion. ;)

Thank you

---

### Post by kerry_s on 2007-06-10
> **DirtDawg said:**
> I have an imac g3 (new gen) that has been running Xubuntu Dapper for about a year now. I've recently been trying to get the 3D acceleration to work, with no luck, and finally borked X to the point where I can't even get a terminal up long enough to run, "sudo cp xorg.conf.bak xorg.conf", if you know what I mean.

Since *buntu dropped their PPC support (BOO!), I've been looking at other distros and Debian looks more and more like a good alternative, but I have just a few questions.

1) Is it true Debian is not really any more difficult to install and set up than *buntu? I would consider myself an intermadiate Linux user as I have been using Linux since 2002, but I still rely heavily on tutorials and howto's for many tasks.

2) Should I use Etch or Lenny? I see Etch has plenty of fans, but I wonder about the "staleness" of the packages. That said, they couldn't really be much older than the Dapper packages I was using anyways, is this correct? In addition, is it possible to, for example, install Lenny packages on an Etch install? The equivalent would be impossible on *buntu.

3) I believe, with an internet connection, if I install the "*xcfe-cd-1.iso", this will install the base system plus xcfe, then get everything else from the internet. Am I correct in this assumtion? In other words, will this be the only cd I need?

4) Is there anything else I should know? I'm close to giving Debian the old college try, but I could use just a little push, or perhaps dissuasion. ;)

Thank you



1) it's the same, they even got a fancy gui installer if you boot with> installgui

2) It's debian, you can combine all the repos and only update what you want or just add the lenny and sid repo, then do a> apt-get dist-upgrade < and just get rid of the etch repo and run lenny/sid for the most up to date system.

3)no, that 1 cd will install the whole xfce system just like xubuntu, it's a 1 cd install.

4) nope, go for it, the only difference you'll notice is debian is faster and requires a bit more tinkering for somethings.

good luck

---

### Post by pelle.k on 2007-06-10
> and finally borked X to the point where I can't even get a terminal up long enough to run, "sudo cp xorg.conf.bak xorg.conf", if you know what I mean.

ever heard of VTs? Ctrl-alt-F2 for exmaple? ;)

---

### Post by DirtDawg on 2007-06-10
> **pelle.k said:**
> ever heard of VTs? Ctrl-alt-F2 for exmaple? ;)

Sure have. Ever heard of the 1/2 hour hang?

---

### Post by DirtDawg on 2007-06-10
> **kerry_s said:**
> 1) it's the same, they even got a fancy gui installer if you boot with> installgui

2) It's debian, you can combine all the repos and only update what you want or just add the lenny and sid repo, then do a> apt-get dist-upgrade < and just get rid of the etch repo and run lenny/sid for the most up to date system.

3)no, that 1 cd will install the whole xfce system just like xubuntu, it's a 1 cd install.

4) nope, go for it, the only difference you'll notice is debian is faster and requires a bit more tinkering for somethings.

good luck

Okay, so as you wrote this I was already torrenting (is that a word?) a copy of the XCFE install CD and was then up until 4 in the AM installing. I've had only a breif time to get aquanted, but so far things look pretty good.

For starters, I screwed up and chose the "net" install, or whatever it's called, and installed the Gnome by mistake. But on a machine that has always ran Xubuntu a bit clunkily, Gnome is running nearly as fast as XCFE did before! Wow! You weren't kidding about Debian being faster. I'm not sure I won't reinstall the XCFE base later, but I certainly have high hopes now.

That said, I can also already tell there's lots of "little" things pre-configured in Ubuntu. For example, Nautilus is quite primative out of the box on Debian. When I open a folder, Nautilus opens a new window every time. I haven't see this behavior since, what, Hoary? Also, there's no side panel/browser as in Ubuntu's Nautilus. There likely a way to get one (I haven't even read any kind of "beginner's guides" yet), but these are kinds of small differences I've observed thus far. 

Otherwise, I'm struck at how amazingly similar to Ubuntu Debian really is! I mean, essentially the same software set, same basic look, same basic behavior. In addition, the default packages are more recent than the Xubuntu Dapper packages from before. Firefox (ok, so "Iceweasel" is a little lame) 2.0 as opposed to Firefox 1.5, for example.

So at this early stage, after playing with it for only about an hour,  I am impressed and excited. But I think I'm going to have some learning to do.

---

### Post by kerry_s on 2007-06-10
Thats okay, the net installer is perfect. With that you can install anything you want. Just do the install but uncheck all the boxes when it comes to that selection, you'll end up with a server/base/minimal install. from there you just reboot after it installs grub and finishes. then->

login as root

nano /etc/apt/sources.list <- you want  to comment out the cdrom, this depends on which net installer you have, the 70mb 1 you can skip this it don't put the cdrom. ctrl+x and y and enter to save.

apt-get update

apt-get install xorg gdm synaptic xfce4 xfce4-appfinder

ctrl + alt + delete to reboot


nautilus, that's what i was talking about, everything will be stock and unmodified just like if you built it yourself. there will be nothing missing or hidden. you can of course just go into the settings and change it so that it is just like in ubuntu.

here's the xfce4 for power pc-> [http://mirrors.kernel.org/debian-cd/current/powerpc/iso-cd/debian-40r0-powerpc-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/powerpc/iso-cd/debian-40r0-powerpc-xfce-CD-1.iso)

so you don't make the mistake, should you want to try it with the debian selection, like i said it's the full setup just like xubuntu.

i always just use the net installer and build up from there, my system is just 450mhz 256ram so i want every inch of speed i can get. ;)

---

### Post by pelle.k on 2007-06-10
> When I open a folder, Nautilus opens a new window every time. I haven't see this behavior since, what, Hoary?
This is called "spatial navigating" and is acctually standard behaviour in vanilla gnome. You have to set "Always open in brower windows" in Edit -> preferences (menu).
Yeah, ubuntu has those little tweaks, but it just a question of learning to do "ubuntu" defaults (if you like how ubuntu does things) yourself.

---

### Post by DirtDawg on 2007-06-11
> **pelle.k said:**
> This is called "spatial navigating" and is acctually standard behaviour in vanilla gnome. You have to set "Always open in brower windows" in Edit -> preferences (menu).
Yeah, ubuntu has those little tweaks, but it just a question of learning to do "ubuntu" defaults (if you like how ubuntu does things) yourself.

Awsome. Thanks for that. :D

---

### Post by DirtDawg on 2007-06-11
> **kerry_s said:**
> Thats okay, the net installer is perfect. With that you can install anything you want. Just do the install but uncheck all the boxes when it comes to that selection, you'll end up with a server/base/minimal install. from there you just reboot after it installs grub and finishes. then->

login as root

nano /etc/apt/sources.list <- you want  to comment out the cdrom, this depends on which net installer you have, the 70mb 1 you can skip this it don't put the cdrom. ctrl+x and y and enter to save.

apt-get update

apt-get install xorg gdm synaptic xfce4 xfce4-appfinder

ctrl + alt + delete to reboot


nautilus, that's what i was talking about, everything will be stock and unmodified just like if you built it yourself. there will be nothing missing or hidden. you can of course just go into the settings and change it so that it is just like in ubuntu.

here's the xfce4 for power pc-> [http://mirrors.kernel.org/debian-cd/current/powerpc/iso-cd/debian-40r0-powerpc-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/powerpc/iso-cd/debian-40r0-powerpc-xfce-CD-1.iso)

so you don't make the mistake, should you want to try it with the debian selection, like i said it's the full setup just like xubuntu.

i always just use the net installer and build up from there, my system is just 450mhz 256ram so i want every inch of speed i can get. ;)


Excellent, thank you. I actually downloaded the correct xcfe-CD-1.iso, but when it asked me about net install I said "yes" and it overrode the default install. I think I'm going to keep Gnome for now since it's really not *that* slow anyways (amazingly), and I figure since I'll probably reinstall anyway, I may as well experiment until something breaks.  :D 

I'm think I'm starting to "get" this distro. It's all about customization and stability, both qualities I'm really learning to appreciate. However, documentation seems more scarce than Ubuntu's. I have yet to find anything as comprihensive and easy-to-understand as Ubuntu's [Desktop Guide]("https://help.ubuntu.com/ubuntu/desktopguide/C/index.html") or [Unofficial Guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"), giving me the feeling that I'm more "on my own." 

I think this will be fun.

---

### Post by kerry_s on 2007-06-11
yep, that's what i would do, just play with it. i'll be back to debian soon, i'm currently just messing around with gutsy, since my friend brought me the net install, my cdr's busted. the more you install debian you'll get use to it. i played with all kinds of setups trying to learn the quirks of this laptop. i was surprised my boot was only 37seconds on this 450mhz, with fluxbox this thing is just fast, faster than my desktop that's still running feisty-xubuntu. i'm already thinking about my next debian setup, so right now i'm just bouncing around the web checking out light weight alternatives, i was thinking of using> apt-get install xorg gdm synaptic fluxbox pcmanfm mousepad  <to start my next install, i like thunar but when i use it with fluxbox it has to many xfce dependencys, so i figure i'll try pcmanfm since it is very similar. :p

anyways, have fun.

---

