---
title: "Let's say I install IceWM from the repos..."
date: 2008-02-22
forum: Desktop Environments
---

### Post by Pogeymanz on 2008-02-22
How much tweaking will I have to do before it becomes fully useable? I'm kind of hoping it has a decent default configuration.

I remember installing one of the *boxes and I couldn't really do anything out of the box.

This is for a friend's computer, so I really don't feel like customizing all day like I would for my own computer.

---

### Post by kerry_s on 2008-02-22
it should be done right out of the box if you do it right.

sudo apt-get install icewm menu
sudo update-menus

then try it

same with the *box's

example:

sudo apt-get install fluxbox menu
sudo update-menus

see here if your doing it from the server install->
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

anything you install will take some setup no matter what it is, especially when your talking wm's verses de's, wm's are made to setup the way you want it using what you want, a de has a set standard for the setup and you have no choice.

i would recommend if your doing it for a friend, go with xfce4, it's alot easier to setup and configure

---

### Post by Pogeymanz on 2008-02-22
I would do XFCE4, except that this computer is super-slow and only has 128 or 192 RAM.

So I want to install Xubuntu, but also install IceWM so that he has options. Yay Linux.

EDIT: Also, thanks for that tip about the menus.

---

### Post by CREEPING DEATH on 2008-02-23
Do a CLI install and XFCE4 from the repos, or just use the Debian XFCE disk - it has a lot less bloat.

CD

---

### Post by kerry_s on 2008-02-23
> **EmosSuck777 said:**
> I would do XFCE4, except that this computer is super-slow and only has 128 or 192 RAM.

So I want to install Xubuntu, but also install IceWM so that he has options. Yay Linux.

EDIT: Also, thanks for that tip about the menus.


ouch, try the debian xfce4 version.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)
it might be really slow though, but faster than xubuntu.

personally, if i were working with low ram, i would use a debian custom install, but for you and the fact you don't want to spend to much time on it, you should be looking at mini distro's instead.

[http://damnsmalllinux.org/](http://damnsmalllinux.org/)  <would be my first choice
[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)
[http://pcfluxboxos.wikidot.com/](http://pcfluxboxos.wikidot.com/)
etc...
[http://distrowatch.com/](http://distrowatch.com/)

i use a debian custom install on 450mhz 256mb ram.

---

### Post by Pogeymanz on 2008-02-23
The computer does have DSL on it, and it runs fast as anything.

But this friend of mine is new to Linux and I don't want him to be under the impression that Linux is as hard as DSL. In particular, I want him to see synaptic.

So I'm willing to sacrifice some speed for easiness.

How do you do a command-line install? Can you do that from the alternate install CD?

I might just go for that Debian XFCE version if it will be faster. I'll still install IceWM too.

---

### Post by kerry_s on 2008-02-23
> **EmosSuck777 said:**
> The computer does have DSL on it, and it runs fast as anything.

But this friend of mine is new to Linux and I don't want him to be under the impression that Linux is as hard as DSL. In particular, I want him to see synaptic.

So I'm willing to sacrifice some speed for easiness.

How do you do a command-line install? Can you do that from the alternate install CD?

I might just go for that Debian XFCE version if it will be faster. I'll still install IceWM too.


for a command line install go with debian, that way you only have to do it once, it can always be updated with apt-get or synaptic. ubuntu is a snap shot distro, it's always recommended a clean install with each release. debian can always be more up to date.

custom install is actually easy. you'll need a net connection and net installer.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

install the base, that means when it comes to the package selection part uncheck both.

log in as root
apt-get install xorg gdm xfce4 synaptic
reboot(ctrl+alt+delete)
select your wm in gdm menu, log in as user, start synaptic and continue to adding what you want

you can vary the apt-get line for different setups.
examples:
apt-get install xorg gdm icewm menu thunar mousepad iceweasel synaptic

apt-get install xorg gdm fluxbox synaptic rox-filer leafpad iceweasel

i'm a jwm user, i use this to start with
apt-get install xorg synaptic jwm rox-filer leafpad

i don't use a login manager, mine's setup to log me in than startx.

also if you want to be more up to date you can change to the lenny repos, just change were it says "etch" to "lenny" and upgrade( apt-get update && apt-get dist-upgrade )

i use both repos (etch/lenny) because the etch kernel works better for me.

my sources.list:
```

deb http://ftp.debian.org/debian/ etch main contrib non-free  
deb http://ftp.debian.org/debian/ lenny main contrib non-free  

deb http://security.debian.org/ etch/updates main contrib non-free 
deb http://security.debian.org/ lenny/updates main contrib non-free 

```


good luck, let me know if you need anything else.

---

### Post by Paingiver on 2008-02-24
This is a link to install and configure 'pekwm':
[http://ubuntuforums.org/showthread.php?t=662204](http://ubuntuforums.org/showthread.php?t=662204)

And this is for openbox:
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by Pogeymanz on 2008-02-24
Thanks for the excellent advice.

Do you think XFCE4 will be tolerable if I do a custom install like that?

---

### Post by Paingiver on 2008-02-24
I wish it will...
And if you can, you can make an ArchLinux install which will be faster.
By the way what is exact system configuration of your friend's?

---

### Post by K.Mandla on 2008-02-24
> **CREEPING DEATH said:**
> Do a CLI install and XFCE4 from the repos, or just use the Debian XFCE disk - it has a lot less bloat.
+1. Pure XFCE is exceptionally fast; Xubuntu doesn't do it justice.
> **Paingiver said:**
> By the way what is exact system configuration of your friend's?
Probably a good question ... what kind of hardware are we talking about?

---

### Post by Pogeymanz on 2008-02-25
We're talking about a PIII @ ~500MHz, with either 128 or 192MB RAM, depending on whether this 64MB stick I have will work.

It does really well with DSL on it, but his family has a "good" computer with 2GHz and WinXP. So this old computer still gets no love. Not to mention DSL (fluxbox and emelfm) is pretty cryptic for a Windows person.

He was just going to take the 40G hard drive and put it in the "better" computer and then throw the rest of this computer away. But I wouldn't hear it!

---

