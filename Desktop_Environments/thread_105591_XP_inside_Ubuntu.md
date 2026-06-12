---
title: "XP inside Ubuntu"
date: 2005-12-18
forum: Desktop Environments
---

### Post by stiankarlsen on 2005-12-18
Hi. I'm pretty new to linux, been using it for some weeks now.

What I was wondering, is how do one go about to run windows inside Ubuntu?

I've been doing a lot of digging on google and in several forums, but not found a guide I understand.

Basically, what I'm asking, is if someone could be so kind and explain to me how I can get windows running inside ubuntu. Is it possible for the two to share the same files on the harddrive? That would really be a pluss..

Appreciate all help:)

---

### Post by khc on 2005-12-18
vmware

---

### Post by stiankarlsen on 2005-12-18
could you be a bit more specific

---

### Post by stiankarlsen on 2005-12-18
another thing, I just used Gparted to make a 20gig ext3 partition. but how do I access it, I guess its hda1 or something under dev, but its locked down.. help me out will ya

---

### Post by cwaldbieser on 2005-12-18
[QUOTE=stiankarlsen]Hi. I'm pretty new to linux, been using it for some weeks now.

What I was wondering, is how do one go about to run windows inside Ubuntu?

I've been doing a lot of digging on google and in several forums, but not found a guide I understand.

Basically, what I'm asking, is if someone could be so kind and explain to me how I can get windows running inside ubuntu. Is it possible for the two to share the same files on the harddrive? That would really be a pluss..

Appreciate all help:)[/QUOTE]

Not sure if you can do this with Xen, it has been a while, so I forget.  For the other way around (Linux on Windowx), Topologilinux worked admirably for me.

---

### Post by Typhoon on 2005-12-18
Or, if you prefer open source, qemu

Typhoon

---

### Post by adie273 on 2005-12-19
Could try Qemu, its free and i installed Windows XP on my Ubuntu system using it.

I'm new to linux too, only been using it a few months. and first time I tried to installed windows for use in ubuntu, I installed just Qemu alone (There is a Qemu accelerator module called Kqemu aswell) and windows ran very slowly. So I uninstalled it and had to use source code rather than install it from synaptic. And while doing that installed the Kqemu module. So windows sped up to a much more bearable speed.

Here's a website that helped me to install both Qemu and the Kqemu...

[http://oui.com.br/n/content.php?article.21](http://oui.com.br/n/content.php?article.21)

You'll need to go into synaptic and install the linux headers for your current kernel, and some other stuff like 'zlib1g-dev' and possibly 'libsdl1.2-dev' as instructed on the website.

I did have a few problems installing it tho, I had to install GCC 3.3, GCC 3.4 and GCC 4.0 in order to compile it properly for reasons unknown to me, I think I read somewhere its cause you have to compile it with the same GCC version as your kernel was compiled with. but i'm no expert, like I said i've only used it for a few months so i could be sooooo wrong lol.

If you happen to try it and like me have problems compiling it and have to start again, instead of just the './configure' command, use './configure --cc=gcc-3.3' (or 3.4 whatever happens to work).

And in the website where it says to use 'kwrite configure' - If it doesn't work, use 'gedit configure' instead, and continue on as normal. although u may already know all that.

This all took me bout 4 or 5 attempts, but had it done within the hour. Hope this helps in someway.

Good luck

---

