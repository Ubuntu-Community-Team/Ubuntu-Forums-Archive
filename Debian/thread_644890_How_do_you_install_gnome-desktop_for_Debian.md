---
title: "How do you install gnome-desktop for Debian?"
date: 2007-12-19
forum: Debian
---

### Post by jingo811 on 2007-12-19
I read somewhere that you do this if Ubuntu's GDM and Gnome Desktop has been removed by accident.
```
sudo apt-get install gdm ubuntu-desktop
```

Now how do you do that in Debian?
The thing is this I've installed Debian with the Base and Desktop environment successfully on different PC's.  But there's one PC that just won't work when I do it like that.  So some ppl have advised me to just install Base first.  Then when I can run Debian to apt-get install a Desktop environment.

This is what I have tried.
```
$ apt-cache search desktop | more  ; gave me circa 50 pages of desktops.
```

Then I did this.
```
$ apt-get install gnome-desktop-environment
```
And it installed for some 5 minutes on a 45-50 Mbit/sec throughput line.
I tried running X with this but no response so I rebooted.
```
$ startx
```
Did the same thing but got a blue screen (grey screen to be precise) saying X11 isn't configured or something.  I didn't know what to do at this point. :confused:

I also tried this but nothing happens when I run startx.
```
$ apt-get install gnome
```
Somebody, anybody help please.

---

### Post by kerry_s on 2007-12-19
if your starting from base you need to install X.
example:
apt-get install xorg gdm gnome

apt-get install xorg kdm kde

apt-get install xorg gdm fluxbox

etc... just remember xorg is X, it has to be installed before the DE or WM
and it's better to reboot into the login manager instead of startx, you should use the startx if your not using a login manager.

---

### Post by jingo811 on 2007-12-19
Tnx kerry_s I'll try it on my jinxed PC once I've managed to backup everything properly.  My stuff is on a separate /home partition but I don't dare to do the partition stuff just yet without backing up first.

When you say DE=(Desktop Environment) and WM=(Windows Manager)
do you mean this:
[LIST]
[*]WM= gdm, kdm   ; and without GDM I won't have metacity?
[*]DE= gnome, kde, fluxbox
[/LIST]

---

### Post by rsambuca on 2007-12-19
> **jingo811 said:**
> Tnx kerry_s I'll try it on my jinxed PC once I've managed to backup everything properly.  My stuff is on a separate /home partition but I don't dare to do the partition stuff just yet without backing up first.

When you say DE=(Desktop Environment) and WM=(Windows Manager)
do you mean this:
[LIST]
[*]WM= gdm, kdm   ; and without GDM I won't have metacity?
[*]DE= gnome, kde, fluxbox
[/LIST]

I hope you don't mind me jumping in, but gdm and kdm are basically just graphical login managers.

the WM ([Window Managers]("http://xwinman.org/index.php")) are things like icewm, fluxbox, metacity, and many others.

DE (Desktop Environments) are usually comprised of a Window Manager, in addition to icons, toolbars, folders, etc.  The common DE's are Gnome, KDE, and XFCE

---

### Post by tturrisi on 2007-12-19
Don't install gnome-desktop-environment.  The WHOLE desktop-environment is bloated just like ubuntu-desktop.

Instead, install gnome-core.  The gnome-core package gives you the basic desktop as well as the other basic applications.  Build up from there with just what you want.

See my site here that gives some details of what to build:
[http://members.cox.net/tonyt/d830](http://members.cox.net/tonyt/d830)

---

### Post by jingo811 on 2007-12-19
Cool site that will come in handy!
So Compiz Fusion is that considered as a DE or a WM or is it something different like UFO?

I've been taught by the teacher to do this in order to get rid of GDM.
```
su -
apt-get install rcconf
update-rcconf-guide
rcconf  ; untick gdm
shutdown -r now
```
Can't I simply do this in order to get rid of GDM?
```
apt-get --purge remove gdm
shutdown -r now
```

---

### Post by kerry_s on 2007-12-19
if you don't want gdm just don't install it.
example:
apt-get install xorg gnome
exit <-to get out of root
startx

i don't use a log in manager at all, i use rungetty and a bash_profile command.

auto login without manager->

apt-get install rungetty

in /etc/initab change the first getty to this->

```
1:2345:respawn:/sbin/rungetty tty1 --autologin user
```

"user" needs to be your login name.

in ~/.bash_profile
put this->

```
if [ `tty` = "/dev/tty1" ]; then
startx
fi
```

---

