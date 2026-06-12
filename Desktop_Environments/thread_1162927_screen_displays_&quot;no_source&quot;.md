---
title: "screen displays &quot;no source&quot;"
date: 2009-05-18
forum: Desktop Environments
---

### Post by wedgy on 2009-05-18
Hi,

When I boot into ubuntu, in low-graphics mode everything works, but when I install proprietary drivers and reboot, just when the login screen should show, the screen goes black, and I get a message from monitor that there is no source. I tried:
Ctrl-alt-F1, and from there 
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```
with no effect.
Also:
manually editing /etc/X11/xorg.conf, but it's like this:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```
and I don't know how to edit this :(. Pls help.
graph. card - nvidia GF7600gt
edit- I had ubuntu 8.10 when I got this issue, installed Jaunty over it, and the issue's still here.

---

### Post by Kevbert on 2009-05-18
Here's my xorg.conf for a Nvidia 7600 GS:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```
To edit, in terminal enter
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by micio on 2009-05-18
> **wedgy said:**
> 
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection


The driver must be Nvidia :)

Change vesa to nvidia and restart X

---

### Post by wedgy on 2009-05-18
I tried editing xorg.conf as you guys posted, the results are still the same. I'm gonna try reverting to 8.04 and see If that helps.

---

### Post by micio on 2009-05-18
Maybe a stupid question...

have you installed nvidia driver?
Or you running ubuntu with it's own video driver?

---

### Post by Kevbert on 2009-05-18
How did you install the Nvidia driver ?
You can revert to low graphics mode just by removing the line
```
Driver	"nvidia"
```
in xorg.conf.
Then reboot and you'll be in low graphics mode again. To install the restricted display driver go to System-Administration-Hardware Drivers. There should be a driver (180.xx) available. Select and enable this (it may take a while to download). Reboot and you should be OK.

---

### Post by glotz on 2009-05-18
[QUOTE=wedgy]...but when I install proprietary drivers [/quote]> no source
;)

---

### Post by Don1500 on 2009-05-18
> **wedgy said:**
> Hi,

When I boot into ubuntu, in low-graphics mode everything works, but when I install proprietary drivers and reboot, just when the login screen should show, the screen goes black, and I get a message from monitor that there is no source. 

I have the same problem and I'm using an ATI 9600. Be that as it may, this is BOOT we're talking about, the drivers ain't loaded and you using a generic vga driver that will only give you the basics of what you need to see the splash screen and text.

Try, in terminal:```
 sudo gedit /boot/grub/menu.lst
```> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash ***vga=791***  [COLOR="Red"]<=== ADD THIS[/COLOR]

That should get you a splash screen back, but it may not be centered. 
Now try this (Credit to Legace)
> Open Terminal, type in the following, and make sure the x and y values are correct.
```


sudo gedit /etc/usplash.conf 
```> For example, for the resolution 1024X768, the x and y values should be:
```


# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1024
yres=768

```> 
Then save the file and close Text Editor (gedit).

Now, go to Terminal again, and type in the following:

```

sudo update-initramfs -u

```> 
Wait until Terminal is done, and then close the window.

Now make sure that you have a VGA=XXX value that is meant for your resolution in menu.lst. Then reboot, and you should be fine 


I just did this and it works. Through out I used 1024X768 or 791 (16 bit) for the resolution, this worked even though my screen resolution is 1680X1050. I might try higher, but this worked.

---

