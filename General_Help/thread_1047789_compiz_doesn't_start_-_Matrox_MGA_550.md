---
title: "compiz doesn't start - Matrox MGA 550"
date: 2009-01-22
forum: General Help
---

### Post by phonky on 2009-01-22
Hi,

I have been looking for quite some time for advice so far...

I am trying to get compiz on my xubuntu box running.
It has a Matrox MGA G550 AGP graphics card, PIV 1800 MHz, 1GB RAM

this is the output of compiz --replace:
```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: true 
no true found, exiting

```

Sounds like my card is not supported?
I am using LXDE / Openbox, BTW

[http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/]("http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/")

suggests to install xserver-xgl - which is not present in Ibex anymore...

any suggestions?
Thanks!

---

### Post by gettinoriginal on 2009-01-23
Check System, Administration, Software Source to make sure the first 4 boxes are checked, and third party software make sure that all boxes except CD are checked.  If not, check them, then reload, you should then get the xserver-xgl.  You should also check Synaptic to make sure that linux-restricted-extras is installed.

---

### Post by phonky on 2009-01-23
Thanks gettinoriginal

> Check System, Administration, Software Source to make sure the first 4 boxes are checked

They were
> and third party software make sure that all boxes except CD are checked
They were not. Fixed now.
> If not, check them, then reload, you should then get the xserver-xgl
Done, but still no xserver-xgl available. I read somewhere that that package has been dumped in Ibex.
> linux-restricted-extras
Haven't found any package like that, but I installed xubuntu-restricted-extras - didn't help.

any other idea?
Isn't "No whitelisted driver found" meaning that the card is maybe not supported? Thanks for any help

---

### Post by Kevbert on 2009-01-23
Unfortunately Matrox is one of those manufacturers that isn't supported by Compiz-fusion and I believe it doesn't support 3D graphics acceleration.
Regarding sound please enter the following in Applications-Accessories-Terminal and post back
```
lshw -C multimedia

```

---

### Post by phonky on 2009-01-23
OK, means I will abandon compiz dreams...](*,):cry:

Here is the output requested - how does that relate to compiz though?

```
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia audio controller
       product: 82801BA/BAM AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

```

BTW, is there any alternative to compiz-fusion? I heard about xcompmgr. Is that a viable alternative?
Thanks

---

### Post by cb951303 on 2009-01-23
I remember that a lot of modern matrox products doesn't support 3d acceleration. Are you sure that your card does?

---

### Post by phonky on 2009-01-23
From 

[http://www.linuxjournal.com/article/5722]("http://www.linuxjournal.com/article/5722")

the Millennium G550 Dual DVI is a versatile, powerful 2D/3D accelerator


EDIT:
AAArgh, wrong card type...


This info we're looking for:
From 
[http://www.free3d.org/]("http://www.free3d.org/")
Matrox G550 AGP (rev 1) 	 Intel Pentium 4 2.8 GHz (x2) 	 XFree86 4.3.0 	 mga 	 Yes 	 v1.2 	 1280×1024 	 16 	 AGPMode=4 	 685 FPS 

The "Yes" column entry relates to "DRI supported?"; according to the link, :
> DRI stands for Direct Rendering Infrastructure. If a driver supports DRI, then it can provide 3D / OpenGL hardware acceleration

---

### Post by Kevbert on 2009-01-23
> **phonky said:**
> OK, means I will abandon compiz dreams...](*,):cry:

Here is the output requested - how does that relate to compiz though?

```
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia audio controller
       product: 82801BA/BAM AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

```

BTW, is there any alternative to compiz-fusion? I heard about xcompmgr. Is that a viable alternative?
Thanks

OOPS. sorry my mistake.  xcompmgr doesn't do that much.  If you want to do some customization to your desktop you might want to take a look at
[[COLOR="Red"]gnomelook[/COLOR]]("http://gnome-look.org/") especially things like GTK2.x themes, screenlets.

---

