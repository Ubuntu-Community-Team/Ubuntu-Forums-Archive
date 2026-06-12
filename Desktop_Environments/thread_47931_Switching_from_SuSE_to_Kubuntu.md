---
title: "Switching from SuSE to Kubuntu"
date: 2005-07-10
forum: Desktop Environments
---

### Post by gnutux on 2005-07-10
Well, I've been monitoring Kubuntu for a long time and I think I should make the switch, but I have a few concerns.

How do I start a new X session? I ask this because I tried Ubuntu but when I entered xinit, it says that I don't have sufficient access or access denied, even as root.

Can I use VMWare Workstation on Kubuntu and how?

*This is only for my main desktop, I'm not switching for my laptop because Kubuntu doesn't have what I need....

Thanks,
gnutux

---

### Post by cwaldbieser on 2005-07-10
I think you can do something like:

```
$ xinit -- :2
```

Where the number after the colon is the display number.  I get a simple X Session when I do that, but I can start kde or gnome with "startkde" or "gnome-session".

---

### Post by coolclassic on 2005-07-11
try ctrl+alt+F8

---

### Post by t2kburl on 2005-07-11
Yes you can use kubuntu in vmware. Just set up the hard drive as IDE instead of scsi when you set up the virtual machine. Power it on with the cd in the drive (or, better yet, use the ISO on your hard drive as the cdrom initially) and the kubuntu installer will start.

---

### Post by gnutux on 2005-07-11
t2kurl,

 I meant; can VMWare installable ON Kubuntu, not the other way around.

Thanx,

xboxrulz

---

### Post by gnutux on 2005-07-11
ok, I got the X server back in working but WTF? I can't set my resolution to 1280x1024!

Also, where's the kernel source packages anyways?

gnutux

---

### Post by Firetech on 2005-07-11
VMware 5 works if you install the "linux-headers" package for your kernel (E.G. "linux-headers-386" or "linux-headers-k7" etc.)
I didn't get VMware 4 working with anything else than compiling my own kernel, but there are people who managed to do it with the linux-headers package.

---

### Post by t2kburl on 2005-07-11
[QUOTE=gnutux]t2kurl,

 I meant; can VMWare installable ON Kubuntu, not the other way around.

Thanx,

xboxrulz[/QUOTE]

Yes, as said, with the kernel-headers package installed for your running kernel ...
I have 5.0 installed in kubuntu and XP and suse VMs on it
To be honest it was the smoothest Linux host install of vmware I've ever done (as opposed to Suse 9.1, 9.2 Pro and 9.3 Pro)

---

### Post by Firetech on 2005-07-11
[QUOTE=t2kburl]Yes, as said, with the kernel-headers package installed for your running kernel ...
I have 5.0 installed in kubuntu and XP and suse VMs on it
To be honest it was the smoothest Linux host install of vmware I've ever done (as opposed to Suse 9.1, 9.2 Pro and 9.3 Pro)[/QUOTE]
 NOT "kernel-headers", "linux-headers"
kernel-* packages have debian patches.
linux-* packages have ubuntu patches, so it's this one you want.

---

### Post by gnutux on 2005-07-11
can someone really please help me w/ the screen resolution problem! I'm freaking out that Kubuntu can't set the monitor to 1280x1024. This was possible w/ SaX2.

Can anyone help please?

gnutux

---

### Post by t2kburl on 2005-07-12
[QUOTE=gnutux]can someone really please help me w/ the screen resolution problem! I'm freaking out that Kubuntu can't set the monitor to 1280x1024. This was possible w/ SaX2.

Can anyone help please?

gnutux[/QUOTE]

SaX2 is a SuSE tool. You will have to fix your xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo dpkg-reconfigure xserver-xorg
``` 
and be sure to set the resolution values you want.

If you haven't already done so, install your video card's drivers first via synaptic

I'm sure someone will correct me on the exact code for your video drivers, too,  :roll:   but a simple search in synaptic should get you there

If anything goes horribly wrong you can :
```
sudo cp /etc/X11/xorg.conf.custom /etc/X11/xorg.conf
``` 
to get back where you started

---

### Post by gnutux on 2005-07-12
seems like SuSE still tops the chart on my list for which is easier....

Kubuntu (Ubuntu) is 3rd.

gnutux

---

