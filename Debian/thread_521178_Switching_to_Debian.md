---
title: "Switching to Debian"
date: 2007-08-09
forum: Debian
---

### Post by amrclutch1 on 2007-08-09
Well, I am thinking about switching to debian so I can install only the packages I want, without all of these preinstalled packages I don't want. Will I be able to get support here too? I love this community, a lot of people, but I would rather use debian unless there is a way to uninstall everything from ubuntu except the raw packages with a gui, for example, gnome, I think that would be it besides synaptic package manager and everything else in the system menu, would this be possible? Also I have found that when I uninstall an application such as beryl it leaves hidden files laying around, can I prevent this? Thanks in advance.

---

### Post by 505 on 2007-08-09
Ubuntu is based in Debian, so a lot of things that apply to Ubuntu also apply to Debian. In fact, you can install all .deb packages from Debian in Ubuntu. So yes, you would be able to get help with most of the thing.
An advantage of Ubuntu is that packages are newer. If you want to stay on Ubuntu you can install the alternate desktop cd. It allows you to install exactly the packages you want.

---

### Post by amrclutch1 on 2007-08-09
Wow, really? I never knew the alternate CD allowed you to choose what packages you want, thanks for that information.

---

### Post by ZipoTe on 2007-08-09
Try changing to debian. It's ubuntu's father so, why don't you give him a chance? :-P with debian you will learn a lot, and for many things, is more stable than ubuntu. Really, try it :)

---

### Post by kerry_s on 2007-08-09
> **amrclutch1 said:**
> Well, I am thinking about switching to debian so I can install only the packages I want, without all of these preinstalled packages I don't want. Will I be able to get support here too? I love this community, a lot of people, but I would rather use debian unless there is a way to uninstall everything from ubuntu except the raw packages with a gui, for example, gnome, I think that would be it besides synaptic package manager and everything else in the system menu, would this be possible? Also I have found that when I uninstall an application such as beryl it leaves hidden files laying around, can I prevent this? Thanks in advance.

i use debian & i'm here. :) you'll get as much help as you need. you can do a custom install with ubuntu or debian and build your ststem to your needs.

ubuntu> [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

debian is pretty much the same.
[http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)

start the install, when you come to the package selection, uncheck them all. that will give you a base install.
after you reboot, you will be at command line.
just login as root 
apt-get install xorg gdm synaptic (your wm or de)
reboot(ctrl+alt+delete)
select your wm or de in the session menu & login
open synaptic and add what you want

ubuntu likes to add alot of stuff, that arent needed.
debian will only install what you chose, so that means you got to select everything you need, also everything is stock nothing has been changed to make it easier.

remember de's will install alot, if you want full control a wm is your best bet.

---

### Post by Bachstelze on 2007-08-09
Moved to the Other OS section.

---

### Post by amrclutch1 on 2007-08-09
Convincing, more stable, cleaner install, burning debian net install to a cd now :P

---

### Post by amrclutch1 on 2007-08-09
I have a problem, I did apt-get upgrade and noticed it only retrieve 1 byte of data. I tried install xorg gdm and gnome, even a simple package such as localepurge or something I know would work, none do, what do I have to add to my sources.list?

---

### Post by kerry_s on 2007-08-09
> **amrclutch1 said:**
> I have a problem, I did apt-get upgrade and noticed it only retrieve 1 byte of data. I tried install xorg gdm and gnome, even a simple package such as localepurge or something I know would work, none do, what do I have to add to my sources.list?

huh? the net install worked, but apt-get doesn't? 

nano /etc/apt/sources.list

deb [http://mirrors.kernel.org/debian/](http://mirrors.kernel.org/debian/) etch main contrib non-free                
deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib non-free              
                                                                                
deb [http://mirrors.kernel.org/debian/](http://mirrors.kernel.org/debian/) lenny main contrib non-free               
deb [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib non-free

first chance you get grab "mc" fantastic tool, file manager, editor. ( apt-get install mc )

if your going to install gnome just let the installer run all the way through, don't unselect anything, gnome is a full de, just like ubuntu.
for just the base, you need to
apt-get install xorg gdm synaptic gnome-core

---

### Post by amrclutch1 on 2007-08-09
ughh, i don't think im ready for debian yet, it's too hard for me, I just started using ubuntu not too long ago, maybe later ill try it. For now I will just use the Ubuntu Alternate CD. I already broke X trying to install drivers.

---

### Post by psusi on 2007-08-09
You are not going to find any difference between Debian and Ubuntu in this regard.  Both default desktop installs have a sizable default installation base.  If you really want to build a system piecemeal with the absolute minimum number of installed packages, then you should either use debootstrap to build the system instead of the standard installer, or try slackware.

---

### Post by amrclutch1 on 2007-08-09
I want to install ubuntu with nothing except the raw basics, xorg, gnome, synaptic, all of the other tools in system, and nothing in the applications menu.

---

### Post by psusi on 2007-08-09
Then manually bootstrap the system.  Install the debootstrap package on the livecd, format the disk, mount it, and use debootstrap to bootstrap the bare metal install.  Then manually set up grub, reboot, and you should have a bare bones command line from which to install any additional packages desired.

---

### Post by rsambuca on 2007-08-09
> **psusi said:**
> Then manually bootstrap the system.  Install the debootstrap package on the livecd, format the disk, mount it, and use debootstrap to bootstrap the bare metal install.  Then manually set up grub, reboot, and you should have a bare bones command line from which to install any additional packages desired.

Is the end result of a debootstrap installation much different than doing a base system netinstall?

---

### Post by psusi on 2007-08-10
Very much so.  A debootstrap basically only sets up the empty directory tree, installs dpgk, apt, a shell, and I think a few other critical things like init, login, getty... basically the absolute minimum you need to be able to have a running system capable of installing other packages.

---

### Post by rsambuca on 2007-08-10
I started with a debian base installation (sid) and have slowly been adding things as I find I need them.  Kind of an experiment to see if there are any noticeable differences between that and ubuntu for the stuff I do.  Perhaps I'll have to look into this bootstrap thing a little more as I don't really quite "get it" yet!

For instance, how much extra stuff have I installed by doing the base installation versus the bootstrap, and will I end up installing most of it anyways to get a desktop up and running?

Thanks for you info, by the way.

---

### Post by psusi on 2007-08-10
Take a look at [https://wiki.ubuntu.com/SeedManagement](https://wiki.ubuntu.com/SeedManagement)

---

