---
title: "Switching from XFCE to LXDE"
date: 2010-05-03
forum: Desktop Environments
---

### Post by epp on 2010-05-03
There is a meta package that installs the LXDE Desktop Environment on ubuntu.  Currently, I have Xubuntu installed.  If the LXDE packages were also installed, does the system still maintain the regular Xubuntu (with its mouse logo) login screen, or does that also change with LXDE?  

I had used LXDE with a different distro and it was super-fast on a K6-2 system, but with that other distro, it had a generic login screen not relating to any particular desktop environment, but the DE was selectable on it.

Thanks for any information/advice.  :)

---

### Post by phillw on 2010-05-06
Hi,

you can install additional desktops, [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde) gives you a good idea of how to do it - just choose the lxde desktop. As you said, you will see the different DE's selectable.

(As a little note, lxde desktop is not the same as installing lubuntu-desktop, to add the lubuntu desktop & it's programmes you need to follow [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Minimal](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Minimal) follow it from, but including the line sudo add-apt-repository ppa:lubuntu-desktop/ppa)

Regards,

Phill.

---

### Post by epp on 2010-05-30
I sort of answered my own question in another thread...  

I installed XFCE on another system (via the xfce4 and xfce-goodies packages) which had ubuntu as the original distro and it removed the ubuntu branding and logo and replaced it (including login screen) with xubuntu graphics.  

So, it would appear that if I did install LXDE, it would now replace the xubuntu branding with lubuntu's.  :neutral:

---

### Post by AdotB on 2010-05-30
If you install the lxde packages, all branding will stay the same. You will have an option at the bottom of the login screen to switch between desktop environments.

Its the [k|x]ubuntu-desktop packages that change the branding

---

### Post by XubuRoxMySox on 2010-05-31
If you 

```
apt-get install LXDE
```

you will get unbranded LXDE that won't change any branding at all. It simply becomes an option you can select at boot-up.

If you

```
apt-get install lubuntu-desktop
```

It will change your Xubuntu branding to Lubuntu and include all the Lubuntu applications and stuff. LXDE is buggy on my hardware, but simple and fast. 

Enjoy,
Robin

---

### Post by epp on 2010-08-24
Have there been any improvements to LXDE since?  

On my K6-2 box, I have xubuntu installed, but even with this, it's a bit slow.  If I installed GNOME and used that, it would run even slower.

*There was one thing I did not like about LXDE, that was the lack of ability to create a desktop shortcut.  I do not know if this has since changed.*

---

### Post by phillw on 2010-08-25
> **epp said:**
> 
*There was one thing I did not like about LXDE, that was the lack of ability to create a desktop shortcut.  I do not know if this has since changed.*

It *can* be done with the 10.04 lubuntu version, but requires a bit of command line editing, with 10.10 it will be able to be done somewhat easier.

Regards,

Phill.
P.S. I'm referring to lubuntu as the package, not lxde as desktop package upon which it is built, with 10.10 there will be available a 'low fat' version of lubuntu.

---

### Post by SeePU on 2010-08-30
> **epp said:**
> Have there been any improvements to LXDE since?  

On my K6-2 box, I have xubuntu installed, but even with this, it's a bit slow.  If I installed GNOME and used that, it would run even slower.

*There was one thing I did not like about LXDE, that was the lack of ability to create a desktop shortcut.  I do not know if this has since changed.*LXDE as a DE is fine but Lubuntu is pure garbage.

The devs are neglecting the project as there's been virtually NO improvements whatsoever despite reports in bugzilla an Launchpad.

Lubuntu devs or whoever manages the project basically ignore and neglect bugs and issues even when they're reported.

There's several issues including a hibernating issue in which certain laptops 'don't wake' and instead, crash.  There's a terminal window title bar issue which was reported eons ago but Lubuntu/Ubuntu/Canonical has done nothing about it.  

I think Canonical just doesn't want to adopt another project or something? 

I'm not sure what the deal is but Lubuntu is the absolutely WORST LXDE project out there.  You are better off trying Mint LXDE or Debian LXDE as your experience with the LXDE desktop is bound to be MUCH MUCH better.  It will give you a much more accurate experience of what LXDE is like.

---

