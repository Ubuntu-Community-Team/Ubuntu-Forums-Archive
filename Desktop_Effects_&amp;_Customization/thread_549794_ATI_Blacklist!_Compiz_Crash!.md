---
title: "ATI Blacklist! Compiz Crash!"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by deucalion on 2007-09-13
I love compiz! Compiz works on my laptop well with its demute X600 Radeon Mobility card. I updated compiz today, i did an apt-get update and an apt-get dist upgrade, and compiz now says (in terminal) that my ATI Driver is Blacklisted! WTF? and i do not want to use FGLRX because it ***** with my laptop and then even games don't work. not to mention its alot of work setting that driver u w/ an xgl login. Any help? Can i go back or change a setting so im not blacklisted?

Thanks!

---

### Post by Xemanth on 2007-09-13
I have this ati blacklist thing too. :(
Is this problem solved in git?

My compiz version is 0.5.2
GFX chip ATI Mobility Radeon X700 128 MB, chipset RS480
Distribution up to date Kubuntu Gutsy

edit: Could you change your topic: Compiz doesn't crash, its just not starting because of the blacklisted ati driver

---

### Post by hmu on 2007-09-13
Changelog says this is because compiz doesn't work with the rs480 chipset, which the ati driver supplies. Anyone knows a workaround to un-blacklist the driver for those of us who *don't* have a problem?

--edit--

found the solution myself:
edit /usr/bin/compiz, look for the line
 BLACKLIST="nv vga vesa vmware via sis ati"
and remove ati from the list. Relogin and voila!

---

### Post by Forlong on 2007-09-13
The better solution would be editing your xorg.conf

If you're on GNOME:
```
sudo gedit /etc/X11/xorg.conf
```
(replace *gedit* with *kate* or *mousepad* or *nano* or whatever you like)

Then change the line
```
	Driver		"ati"
```
in the *Section "Device"* to
```
	Driver		"radeon"
```
(of course only if your card is [supported](http://xorg.freedesktop.org/archive/X11R7.0/doc/html/radeon.4.html) - it will, if compiz used to work)


But I'm curious - how did you install Compiz?
So which packages are affected by this?

---

### Post by Stemp on 2007-09-13
@Forlong : nope, it's not working... radeon driver must be considered as an ati driver ;)

@hmu : /usr/share/compiz ? I had to modify /usr/bin/compiz 
but anyway thanks for the solution ;)

---

### Post by Amaranth on 2007-09-13
Sorry guys, should have a proper fix in very soon today.

---

### Post by hmu on 2007-09-13
> **Stemp said:**
> 

@hmu : /usr/share/compiz ? I had to modify /usr/bin/compiz 


Effffff, yes, sorry, fixed my post :-)

---

### Post by Forlong on 2007-09-13
> **Stemp said:**
> @Forlong : nope, it's not working... radeon driver must be considered as an ati driver ;)
Did you restart your X-Server? If you change your xorg.conf you'll always have to do that, before the settings will take effect (sorry for not pointing that out earlier).

---

### Post by Stemp on 2007-09-13
> **Forlong said:**
> Did you restart your X-Server? If you change your xorg.conf you'll always have to do that, before the settings will take effect (sorry for not pointing that out earlier).

Yes I did : 

```
stemp@caderousse:~$ cat /var/log/Xorg.0.log | grep radeon
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
(II) ATI: ATI driver wrapper (version 6.6.193) for chipsets: mach64, rage128, radeon
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Reloading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"

```

---

### Post by deucalion on 2007-09-14
Update came out and my driver is now working. it was not a problem with mt X-Server. when the update came out last night, and asked for the system restart, i did, and low and behold it was working again! good to know there is a Radeon driver too! is it any better than the ATI driver?

---

### Post by Forlong on 2007-09-14
> **deucalion said:**
> good to know there is a Radeon driver too! is it any better than the ATI driver?
No, the ati driver is kind of a "meta driver" that takes care your card uses the best driver available. So if your card is supported by the radeon driver you already used it before.

I just thought you could trick the blacklist by changing the xorg.conf to specifically use the open radeon driver.

---

### Post by Stemp on 2007-09-14
> **deucalion said:**
> good to know there is a Radeon driver too! is it any better than the ATI driver?

The ati driver depending on your card use the 'atimisc', 'r128' or 'radeon' sub-drivers ;)

[QUOTE=Forlong]I just thought you could trick the blacklist by changing the xorg.conf to specifically use the open radeon driver.[/QUOTE]

Yes it was a good idea, still wondering why it's not working.

---

