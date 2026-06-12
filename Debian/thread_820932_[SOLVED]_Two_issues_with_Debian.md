---
title: "[SOLVED] Two issues with Debian"
date: 2008-06-06
forum: Debian
---

### Post by Inxsible on 2008-06-06
I just converted over from Xubuntu to Debian Xfce. But I have these two issues.

1) I installed with debian-testing-xfce, but it has still installed Gnome and TWM. How would I remove everything related to gnome and twm and get pure Xfce. In ubuntu, we can simply remove xubuntu-desktop and be done with it. Is there something similar in Debian?

2) I don't get any video playback. I tried it and it asked me if I wanted to download and install the codecs to which I said Yes..But it still doesn't play video. It plays the sound though. My mp3s work too.


And its funny...ubuntu is based on Debian..but Xubuntu ran extremely slow on my machine...but in Debian -- even Gnome was pretty smooth without any lags. Of course I dare not enable the effects on this P3-1.1GHz, 256MB RAM, 32 MB shared nVidia

Thanks.

---

### Post by SunnyRabbiera on 2008-06-06
I am sure you can just remove the gnome desktop files via synaptic like you would do in ubuntu but you need to remove the packages manually if I remember right.
as for multimedia, I know debian has its own media repository though I forget what its called now.

---

### Post by Inxsible on 2008-06-06
I just went into Synaptic and am uninstalling everything that's related to gnome from under the section 'GNOME Desktop Environment'. Hopefully that should get rid of all things Gnome.

---

### Post by kerry_s on 2008-06-06
what media player are you using?

also where did you get the testing xfce4?
i only grab straight from debian->
[http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/)

xfce on the bottom

---

### Post by Inxsible on 2008-06-06
> **kerry_s said:**
> what media player are you using?

also where did you get the testing xfce4?
i only grab straight from debian->
[http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/)

xfce on the bottomI was using the one from debian as well. and I was using totem as my media player.

---

### Post by Inxsible on 2008-06-06
I just uninstalled all gnome apps including gdm which got removed when I selected a few others.

This is nice. I login at CLI and then simply issue startx -- which I am going to put in a bash_profile. so it should be all good.

However, I seem to have lost my root privs - as in I had put myself in sudoers before I uninstalled Gnome. After removing Gnome, when I tried to open Synaptic, it opened up a terminal where I had to enter the root password. 

I checked the sudoers.tmp again and my user name is in the file. Do I have to do something else for it to NOT ask me the root password and just make do with my user password?

---

### Post by kerry_s on 2008-06-06
change the launcher to use "sudo synaptic".

i use mine with out having to type the password:

```
user    ALL=NOPASSWD: /sbin/reboot, /sbin/halt, /usr/sbin/synaptic, /usr/bin/renice
```

here's what i have set to sudo with no password.

---

### Post by Inxsible on 2008-06-07
> **kerry_s said:**
> change the launcher to use "sudo synaptic".

i use mine with out having to type the password:

```
user    ALL=NOPASSWD: /sbin/reboot, /sbin/halt, /usr/sbin/synaptic, /usr/bin/renice
```here's what i have set to sudo with no password.Thanks kerry. I tried using it the way you have it - without password., but it doesn't work for me. When I start synaptic I get a root terminal where I need to enter the password.

I guess that's probably because I got rid of gksudo along with gnome apps. Does xfce have its own graphical sudo ?

---

### Post by Inxsible on 2008-06-07
Yet another issue is that my Quit button doesn't ask for confirmation at all. It simply logs me out. So now I cannot reboot or shutdown.

Why would that change all of a sudden? It worked when Gnome was installed. :(

---

### Post by kerry_s on 2008-06-07
boy you are just not having any luck. :lolflag:

for synaptic, in /usr/share/applications you'll find "synaptic.desktop" open that with your text editor.
change:
Exec=su-to-root -X -c /usr/sbin/synaptic
to
Exec=sudo /usr/sbin/synaptic

then you can use the nopasswd.

the xfce4 shutdown fix is here->
[http://wiki.xfce.org/faq](http://wiki.xfce.org/faq)

oops, i think i misunderstood the quit problem, look in the settings-session(?) and change it to ask.

---

### Post by Inxsible on 2008-06-07
> **kerry_s said:**
> boy you are just not having any luck. :lolflag:

for synaptic, in /usr/share/applications you'll find "synaptic.desktop" open that with your text editor.
change:
Exec=su-to-root -X -c /usr/sbin/synaptic
to
Exec=sudo /usr/sbin/synaptic

then you can use the nopasswd.

the xfce4 shutdown fix is here->
[http://wiki.xfce.org/faq](http://wiki.xfce.org/faq)

oops, i think i misunderstood the quit problem, look in the settings-session(?) and change it to ask.
Yeah. I think at this point I'll just go ahead and install Debian netinst. This Debian Xfce was just a trial run anyway -- a comparison of Debian vs Xubuntu.

Oh and I did try the no password after changing the .desktop to sudo. No love. :(

---

### Post by Barrucadu on 2008-06-07
You've lost GDM and Ggksudo and suchlike because they're all parts of GNOME. XFCE doesn't have it's own login manager, but you could use an alternative to GDM and KDM such as XDM or SLiM

---

### Post by Inxsible on 2008-06-07
> **Barrucadu said:**
> You've lost GDM and Ggksudo and suchlike because they're all parts of GNOME. XFCE doesn't have it's own login manager, but you could use an alternative to GDM and KDM such as XDM or SLiM
Yeah I know that. I am currently using SLiM. But I think I will go back to a simple CLI login and having a bash_profile starting up my X.

---

### Post by Inxsible on 2008-06-07
Ok. I am currently installing Debian Xfce again and this time I selected not to install from a network mirror - hoping that since its a Debian Xfce CD, choosing from the Cd will only install Xfce apps.

But the install is currently at 51% and I just saw gnome-keyring being installed...

So I guess this doesn't look good. Its probably going to install Gnome and TWM again.

alrite....on to the Debian netinst then...... ;)

---

### Post by Inxsible on 2008-06-07
Looks like I was half correct. It did not install Gnome, but it did install TWM.

However, TWM is just a single package and easily removable :D. Finally I have my pure Xfce desktop.

---

### Post by Arthur Archnix on 2008-06-07
I did a net install of Lenny, started with fluxbox but decided I didn't want to do that much work. So I removed it and installed xfce4. That pulled in some dependencies but gave me a working and pretty xfce desktop. I say forget about synaptic and just use aptitude. At the cli as root type synaptic. Hit F1 to learn some of the shortcuts. 

These are the dependencies that are pulled in if I install synaptic:
> The following NEW packages will be installed: deborphan docbook-xml gksu libcairo-perl libgksu2-0 libglib-perl libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgtk2-perl libgtop2-7 libgtop2-common libscrollkeeper0 scrollkeeper sgml-data sudo synaptic

I chose no. :P

---

### Post by Inxsible on 2008-06-07
Ok. Since I installed Debian Xfce (only from CD- as opposed to from a network mirror), I do not have Synaptic at all.

Also I cannot use apt-get to install anything from the command line. This is what i get if I try to install anything from CLI```
# apt-get install pmount
Reading package lists...Done
Building dependency tree
Reading state information...Done
Package pmount is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package pmount has no installation candidate
#
```This happens not only with pmount, but also when i try to install synaptic.

](*,)

---

### Post by kerry_s on 2008-06-07
> **Inxsible said:**
> Looks like I was half correct. It did not install Gnome, but it did install TWM.

However, TWM is just a single package and easily removable :D. Finally I have my pure Xfce desktop.

well in the past twm was part of xorg, perhaps someone felt like including it again. :)

---

### Post by Arthur Archnix on 2008-06-07
Check your sources list. Make sure you apt-get update. You can search for package names by doing something like:
```
apt-cache search synaptic
```
Or you can just type ```
aptitude
```, and browse through like you would in synaptic by category, installed, etc... aptitude show is also very useful. I ran it and here's what I got:
> debian:/# aptitude show pmount
Package: pmount
State: not installed
Version: 0.9.17-2
Priority: optional
Section: utils
Maintainer: Vincent Fourmond <fourmond@debian.org>
Uncompressed Size: 496k
Depends: libblkid1 (>= 1.39-1), libc6 (>= 2.7-1), libdbus-1-3 (>= 1.1.1), libhal-storage1 (>= 0.5.10), libhal1 (>= 0.5.10), libsysfs2
Suggests: cryptsetup (>= 1.0), hal
Description: mount removable devices as normal user pmount is a wrapper around the standard mount program which permits normal users to mount removable devices without a matching /etc/fstab entry. This provides a robust basis for automounting frameworks like GNOME's Utopia project and confines the amount of code that runs as root to a minimum. 
 
This package also contains a wrapper "pmount-hal" which reads some information like device labels and mount options from hal and passes them to pmount.

**Install the package "hal" if you want to use this feature. **
 
If a LUKS capable cryptsetup package is installed, pmount is able to transparently mount encrypted volumes.

---

### Post by kerry_s on 2008-06-07
> **Inxsible said:**
> Ok. Since I installed Debian Xfce (only from CD- as opposed to from a network mirror), I do not have Synaptic at all.

Also I cannot use apt-get to install anything from the command line. This is what i get if I try to install anything from CLI```
# apt-get install pmount
Reading package lists...Done
Building dependency tree
Reading state information...Done
Package pmount is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package pmount has no installation candidate
#
```This happens not only with pmount, but also when i try to install synaptic.

](*,)


to me it sounds like there's problems with the lenny-xfce4 installer, i would try the etch-xfce4 installer which can be upgraded to lenny afters.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

you simply, change etch to lenny in /etc/apt/sources.list

by the way a default debian install does not usually have synaptic, i've always had to install it after.

---

### Post by Inxsible on 2008-06-07
Thanks Arthur, I do know about those commands, but none of them work and I think I know why> **kerry_s said:**
> to me it sounds like there's problems with the lenny-xfce4 installer, i would try the etch-xfce4 installer which can be upgraded to lenny afters.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

you simply, change etch to lenny in /etc/apt/sources.listI think you are right...its probably an issue with the Lenny xfce installer. somebody@debian created the Xfce iso in a hurry :(


> **kerry_s said:**
> by the way a default debian install does not usually have synaptic, i've always had to install it after.  And Aha !!! I didn't know that. I guess when I first installed it - it installed Gnome and it gave me Synaptic as well...so I assumed the "only" xfce would have it too. :(


Now I just checked the apt/sources.list and guess what....I think i am missing repos. As of now it only says ```
 # 
# deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot i386 xfce-CD Binary-1 20080314-21:59]/ lenny main

deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot i386 xfce-CD Binary-1 20080314-21:59]/ lenny main

deb http://security.debian.org/ lenny/updates main
deb-src http://security.debian.org/ lenny/updates main

``` which means I am missing the  main repos. Could one of you post your sources.list for lenny ?

This is the first time I opened the sources.list file. I haven't tinkered with it at all in this new install..honest !! so I don't know why it is missing the main repos.

---

### Post by Arthur Archnix on 2008-06-07
Here is my Lenny sources list... note however that I am using the Finland repos, so don't just straight copy mine. Just use it to modify your own.
> debian:/# cat /etc/apt/sources.list
deb [http://ftp.fi.debian.org/debian/](http://ftp.fi.debian.org/debian/) lenny main contrib non-free
deb-src [http://ftp.fi.debian.org/debian/](http://ftp.fi.debian.org/debian/) lenny main contrib non-free

deb [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib non-free
deb-src [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib non-free

---

### Post by Inxsible on 2008-06-07
> **Arthur Archnix said:**
> Here is my Lenny sources list... note however that I am using the Finland repos, so don't just straight copy mine. Just use it to modify your own.Thanks Arthur Archnix, I guess i will simply use the US mirrors..

---

### Post by Inxsible on 2008-06-07
And Houston, we have liftoff !!!!

---

