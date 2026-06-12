---
title: "Exporting XFCE look &amp; feel?"
date: 2006-12-29
forum: Desktop Environments
---

### Post by lkvee on 2006-12-29
I've grown accustomed to using the look and feel provided by xfce in xubuntu.

I've recently 'net installed debian on a laptop with no CD-ROM drive.   I'm thinking about using xfce as the regular desktop (fluxbox's the other choice).   I'd much rather see the layout provided by xubuntu over that of debian.

How do I export xubuntu's xfce to my debian laptop?   I'm not sure if I need to install other packages, but since the laptop's not powerful, I wasn't planning on using stuff like conky, torsmo, or adesklets.

Thanks for reading!

---

### Post by kerry_s on 2006-12-29
I'm not sure i understand your question? If your talking about installing a xubuntu like desktop it would just be xfce4( sudo apt-get install xfce4 ) Now if your talking about the custom look of xubuntu, you'll probably just have to copy them over to the debian desktop. The easy way would probably be by using the live cd . Most of it is stock xfce4 but there are some xubuntu specific parts like the splash screens & the default look. Just go for your own look, like for instance the splash screen after the gdm, if you click on simple & configure you can set the font size you want & the image you want, then you'll have your own custom splash screen. Just play with it enjoy.

---

### Post by lkvee on 2006-12-29
I installed debian because xubuntu does not feature net installation.   I had to use a net install because this laptop doesn't have a CD-ROM drive.   SBM does not recognize a USB CD-ROM on this laptop either.   Using Xubuntu Live's a near impossibility.

However, I like the panels featured in xubuntu and want to use them in my debian laptop.

I still want to know the best way to export xubuntu's xfce theme into a debian laptop with xfce installed.

---

### Post by kerry_s on 2006-12-29
All right if you just must, try this, grab the xubuntu-default-settings.deb and see if it will install on debian. I'm not sure witch debian version your using so here's the page with all of them (0.24would be feisty, 0.23 is edgy,...)
-> [http://mirror.linux.org.mt/mirror/ubuntu/packages/pool/main/x/xubuntu-default-settings](http://mirror.linux.org.mt/mirror/ubuntu/packages/pool/main/x/xubuntu-default-settings)

---

### Post by Roderik on 2006-12-30
as far as i know you could also just take a sources.list from a xubuntu pc and put that on the debian machine. apt)get update and apt-get dist-upgrade, apt-get install xubuntu-desktop and ypu're done

---

### Post by kerry_s on 2006-12-30
> **Roderik said:**
> as far as i know you could also just take a sources.list from a xubuntu pc and put that on the debian machine. apt)get update and apt-get dist-upgrade, apt-get install xubuntu-desktop and ypu're done

Only if you like breakage. You know there is a difference right?

---

### Post by 3rdalbum on 2006-12-30
Copy the ~/.config from your Xubuntu machine to the same location on Debian. Log into XFCE and everything should look right!

---

### Post by Roderik on 2006-12-31
> **kerry_s said:**
> Only if you like breakage. You know there is a difference right?

it worked fine during the days of hoary when i switched to ubuntu :)

---

### Post by kerry_s on 2006-12-31
> **Roderik said:**
> it worked fine during the days of hoary when i switched to ubuntu :)

Well if you've done it, it must work. :D

---

