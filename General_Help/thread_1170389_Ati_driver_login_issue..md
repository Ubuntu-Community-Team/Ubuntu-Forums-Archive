---
title: "Ati driver login issue."
date: 2009-05-26
forum: General Help
---

### Post by Kaneda187 on 2009-05-26
When i have the ATI driver from the repos installed i cant get to my login screen, all i get is a black screen with odd pixelated colours I never had this issue before its an old enough video card.
This to be exact:

ATI Mobility Radeon X1400

Any help would be great Thanks

---

### Post by pro003 on 2009-05-26
you need to remove that driver and to do that reboot and enter in Repair mode, drop to root shell with networking, and remove the fglrx driver, just type

```
sudo aptitude search fglrx
```

it will show you installed packages which begins with word fglrx

```
sudo apt-get remove --purge fglrx*
```

then set up default xorg.conf
```

cd /etc/X11
rm -r xorg.conf
cp xorg.conf-original xorg.conf
sudo reboot
```

download the driver from [ati's]("http://ati.amd.com") site and try your like with it.

---

### Post by tommah04 on 2009-05-26
the same thing happened to me...
 
and its probably due to ati not supporting that card under ubuntu....at least that's what someone told me, but I have a x1300
 
so I dunno if its compatible or not

---

### Post by Legace on 2009-05-26
The new FLGRX driver is not compatible with your graphics card. You need to use the opensource radeon driver instead.. To remove the FGLRX driver:

> **gocek said:**
> Reboot PC and select "recovery mode" in boot-manager (GRUB) and then go for "root shell" option. 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```


then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

---

### Post by tommah04 on 2009-05-26
so an opensource driver will work? where could I find that?

---

### Post by Kaneda187 on 2009-05-27
I got the driver from synaptic packet manager and it works fine thers a few different ones in ther that gave me the some problem but the i just boot in to recovery mode and removed them via shell!
thanks guys!

---

