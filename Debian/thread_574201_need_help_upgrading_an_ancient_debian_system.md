---
title: "need help upgrading an ancient debian system"
date: 2007-10-12
forum: Debian
---

### Post by 900donuts on 2007-10-12
this is an off shoot of this thread [http://ubuntuforums.org/showthread.php?t=569167](http://ubuntuforums.org/showthread.php?t=569167) as you would read some where in between the 50th and 60th post i replaced the hp omnibook's hard drive with one that from a dead laptop i got from my uncle that i pleasantly found had debian already installed but the version is 3.0 woody and i'm a little lost on how to upgrade it to at least 3.1 sarge 

could somebody help me?

---

### Post by ryno519 on 2007-10-12
It should be as easy as changing the entries in your sources.list. If I were you I'd probably upgrade to Etch or maybe even Lenny (testing). It's really quite easy. I'd imagine you just want the latest stable version of Debian.

Before you do this make sure you have a Debian/Ubuntu/Whatever install disk in case something goes wrong during the update. At least download and burn the Debian Etch NetInst CD so you can quickly install a working system. However, my experience with Debian updates is that they're usually pretty smooth. This is just a precaution.

Open a terminal and become root.

```

cd /etc/apt/
cp sources.list sources.list.bak
gedit sources.list

```

Once into the sources.list file you will want to delete everything in there and replace it with this.

> 
# Stable Etch
 deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) stable main contrib non-free 
# Stable Sources
 deb-src [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) stable main contrib non-free 


After this you will want to run the following commands. If the first command tells you you already have aptitude, just ignore it and go on.

Still as root,

> 
apt-get update
apt-get dist-upgrade


The upgrade should give you a LONG list of software that needs to be updated. Let it run, restart and make sure everything is working.

---

### Post by rsambuca on 2007-10-12
I think it may just be easier to do the netinstall to customize it for your own needs.

---

### Post by ryno519 on 2007-10-12
> **rsambuca said:**
> I think it may just be easier to do the netinstall to customize it for your own needs.

I didn't find the netinstall extraordinarilly customizable.

---

### Post by rsambuca on 2007-10-12
> **ryno519 said:**
> I didn't find the netinstall extraordinarilly customizable.

Huh?

You just install the bare minimum and then add on what you need.  That is the ultimate in customizable!

---

### Post by ryno519 on 2007-10-12
> **rsambuca said:**
> Huh?

You just install the bare minimum and then add on what you need.  That is the ultimate in customizable!

Well, maybe I didn't get into it too deep, but when I was installing it I had maybe seven options I could enable or disable, all of which would be easy enough to get through the repositories.

---

### Post by kerry_s on 2007-10-12
go custom.
[http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)

when it comes to package selection, uncheck all of them, that will give you a base install. on reboot->
log in as root
apt-get xserver-xorg-video-vesa xorg jwm mc dillo
reboot(ctrl+alt+delete)
log in as your user
startx


xserver-xorg-video-vesa xorg=pretty bare X
jwm=window manager
mc= file manager, editor
dillo=web browser

it can be done, i use the same to start my build, except for vesa i use neomagic and dillo i use iceweasel, but you don't meet the recommends for that, i'm using pcmanfm for my file manager.

with iceweasel open i'm at 40+mb,most of which is cache, on first startup i'm at 16mb used.

---

### Post by kerry_s on 2007-10-12
my heart goes out to you, for wanting to use that computer.
i just tried mine with 32mb ram and boy does it suck.
i recommend you skip X all together and just go with->

[B]apt-get install mc links2
links2 -g google.com[/B]

learn to use the command line and console based app's.

here's a pic, to show it can be done, just don't think it's worth it. just to see what would happen if i try to open iceweasel, it crashed my computer. :lolflag:

---

### Post by 900donuts on 2007-11-01
it been a while since i worked on the omnibook (freakish school block schedule+midterms don't ask) but during the past 2 week i was able to perform a debian floppy install and "apt-get" mc and links2  but some error came up as a result

 dpkg: failed to write status record about "pcmciautils" to "var/lib/dpkg/status": no space left on device
E: Sub-process /usr/bin/dpkg returned an error code (2)

the computer still seemed to work i tried out mc and links2 and then tried to install x and jwm and got back this

E: dpkg was interrupted, you must manually run "dpkg --configure -a" to correct the problem

so i typed dpkg --configure -a and got back this

 dpkg: failed to write status record about "pcmciautils" to "var/lib/dpkg/status": no space left on device

my questions are
1.what dose all this mean
2.what is the problem
3.if its my fault what i did i do wrong
4.and how do i fix this

p.s. if it matters i haven't turned the machine off yet

---

### Post by 900donuts on 2007-11-08
since no one provided a better option i had no choice but to reinstall debian and do the partitioning right i decided to continue the discussion here

[http://forums.debian.net/viewtopic.php?t=21004](http://forums.debian.net/viewtopic.php?t=21004)

 since all interest seems to have left due to my inconsistency in posting

---

