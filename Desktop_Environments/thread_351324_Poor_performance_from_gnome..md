---
title: "Poor performance from gnome."
date: 2007-02-01
forum: Desktop Environments
---

### Post by emachine on 2007-02-01
I am getting very sluggish behavior from gnome.  In Firefox if I scroll my mouse I can see the refresh.  If I drag a window over another window I can see the refreshing. When I my processes using top I can watch xorg absolutely thrash my CPU.

I've rebuilt my kernel to use my processor (P4) family from the guides in this forum and still no real gain. 

My current screen res is 1600x1200 @ 66hz.  This is under the native resolution of my 24" wide flat panel.  I would like to get this fixed up and get Gnome running a bit faster.  Any advice would be greatly appreciated.

-Toby

---

### Post by emachine on 2007-02-01
> **emachine said:**
> I am getting very sluggish behavior from gnome.  In Firefox if I scroll my mouse I can see the refresh.  If I drag a window over another window I can see the refreshing. When I my processes using top I can watch xorg absolutely thrash my CPU.

I've rebuilt my kernel to use my processor (P4) family from the guides in this forum and still no real gain. 

My current screen res is 1600x1200 @ 66hz.  This is under the native resolution of my 24" wide flat panel.  I would like to get this fixed up and get Gnome running a bit faster.  Any advice would be greatly appreciated.

-Toby

Well I am pretty sure I figured out what the problem is, now only how to fix it.  I open /etc/X11/xorg.conf and found that my device is set to:

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection


I have an S3 Graphic UniChrome Pro IGP, how do I install a driver for it?

---

### Post by emachine on 2007-02-01
> **emachine said:**
> Well I am pretty sure I figured out what the problem is, now only how to fix it.  I open /etc/X11/xorg.conf and found that my device is set to:

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection


I have an S3 Graphic UniChrome Pro IGP, how do I install a driver for it?

I've done some searching found [this installation guide]("http://http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/") to install a driver for my VIA P4M800 (yay)
So, I am working through it everything is fine until I run ./makedriver

I get this this error:

```
cp: target `/usr/src/xc/programs/Xserver/hw/xfree86/drivers/' is not a directory: No such file or directory
./makedriver: line 359: cd: /usr/src/xc/programs/Xserver/hw/xfree86/drivers/via: No such file or directory
make: *** No rule to make target `Makefile'.  Stop.
chmod: cannot access `mpatch': No such file or directory
./makedriver: line 391: ./mpatch: No such file or directory
make: *** No rule to make target `clean'.  Stop.
cp: cannot stat `via_drv.o': No such file or directory
 -------- Complete to make & copy driver --------
```

I'm getting a little bit frustrated trying to fix this so any help would be appreciated.

-t

---

### Post by emachine on 2007-02-01
> **emachine said:**
> I've done some searching found [this installation guide]("http://http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/") to install a driver for my VIA P4M800 (yay)
So, I am working through it everything is fine until I run ./makedriver

I get this this error:

```
cp: target `/usr/src/xc/programs/Xserver/hw/xfree86/drivers/' is not a directory: No such file or directory
./makedriver: line 359: cd: /usr/src/xc/programs/Xserver/hw/xfree86/drivers/via: No such file or directory
make: *** No rule to make target `Makefile'.  Stop.
chmod: cannot access `mpatch': No such file or directory
./makedriver: line 391: ./mpatch: No such file or directory
make: *** No rule to make target `clean'.  Stop.
cp: cannot stat `via_drv.o': No such file or directory
 -------- Complete to make & copy driver --------
```

I'm getting a little bit frustrated trying to fix this so any help would be appreciated.

-t
I've managed to work through the first error which was caused by the makefile referencing the stock kernel name (guess thats what I get for recompiling mine)

I fixed this by editing this line in the makedriver makefile:

```
if [ "$KERNELVERSION" = "2.6.15-1.2054_FC5" ] || [ "$KERNELVERSION" = "2.6.15-1.2054_FC5smp" ] || [ "$KERNELVERSION" = "2.6.18-1.2798.fc6" ] || [ "$KERNELVERSION" = "2.6.18-1.2798.fc6.cx700" ] || [ "$KERNELVERSION" = "2.6.17-5mdv" ] || [ "$KERNELVERSION" = "2.6.17-5mdventerprise" ] || [ "$KERNELVERSION" = "2.6.15-26-386" ] || [ "$KERNELVERSION" = "2.6.17.14-ubuntu1-custom" ];
```

I simply over wrote the 2.6.17.14-generic with mine.

Now I am still getting this error: cp: cannot stat `via_drv.o': No such file or directory
I am starting to think that I need to move the XServer source code somewhere but that will require more research.

-t

---

### Post by denes on 2007-03-17
Hi, I have the same problem, however some months ago I could fix it.

---

### Post by denes on 2007-03-17
Hi, I could solve the problem. You just have to change the kernel's version everywhere (in the makedriver and in the vinstall_2d)

---

