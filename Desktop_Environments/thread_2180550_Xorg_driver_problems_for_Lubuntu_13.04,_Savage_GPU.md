---
title: "Xorg driver problems for Lubuntu 13.04, Savage GPU"
date: 2013-10-13
forum: Desktop Environments
---

### Post by Beeblebrx on 2013-10-13
I just installed Lubuntu 13.04 on an old laptop (i386_pentium_256 RAM). The GPU on this box is S3_SavageIX-MV_rev-11. My problem is that I cannot get a decent Xorg setup - no acceleration and the result is a system which rapidly chokes on resources. I was barely able to get a GUI login screen by setting "Driver  vesa" in /etc/X11/xorg.conf.  What I get for "Xorg -configure" is below (clipped).

```
[   432.225] (EE) open /dev/dri/card0: No such file or directory
[   432.225] (WW) Falling back to old probe method for modesetting
[   432.225] (EE) open /dev/dri/card0: No such file or directory
[   432.225] (WW) Falling back to old probe method for vesa
[   432.225] (WW) Falling back to old probe method for fbdev
[   432.225] (II) Loading sub module "fbdevhw"
[   432.225] (II) LoadModule: "fbdevhw"
[   432.226] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   432.244] (II) Module fbdevhw: vendor="X.Org Foundation"
[   432.244]     compiled for 1.13.3, module version = 0.0.2
[   432.244]     ABI class: X.Org Video Driver, version 13.1
[   432.244] (EE) open /dev/fb0: No such file or directory
[   432.245] Number of created screens does not match number of detected devices.
  Configuration failed.
```

```
# apt-get install xlibmesa-dri
Package xlibmesa-dri is not available but is referred to by another package. The following packages replace it: libg11-mesa-dri
E: Package xlibmesa-dri has no installation candidate

# apt-get install libg11-mesa-dri
E: Unable to locate package libg11-mesa-dri
```

Please advise how to solve this problem in Ubuntu.

---

### Post by ajgreeny on 2013-10-13
I think 256 MB ram is your problem with this latest version of Lubuntu; more would help terrifically I believe, though I accept that your GPU is also not helping.

---

### Post by Rex Bouwense on 2013-10-13
+1.  Although it is reported that you only need 192 Mbs to install and run Lubuntu, I believe that you need more or the advantage of a super fast less resource hungry OS disappears.  Besides RAM is really inexpensive now and more will give you a better Lubuntu experience.

---

### Post by Beeblebrx on 2013-10-14
The box is an old laptop, with maxed-out RAM slots - not possible to add more, not possible to find the RAM modules even if I had the space.

I disagree with your RAM requirement assessment. I had Backtrack R2 (which is based on 12.04 precise, if I recall correctly) installed on that laptop and the graphics worked fine. The only reason I switched to Lubuntu was to eek out a little more performance from the unit. I unfortunately made the stupid mistake of not taking a copy of the working xorg.conf I had on that version, but then again, who could have known?

The key to the problem at hand, in my opinion is this little gem:
```
(EE) open /dev/dri/card0: No such file or directory
```
The drivers providing mesa-dri acceleration for this card are provided and exist on the Xorg wiki page. I just need to figure out why Lubuntu is not providing the correct drivers. Perhaps an "apt-add repository"?

**EDIT:** I seem to have neglected to state the obvious: A missing [COLOR=#0000ff]**/dev/dri**[/COLOR] folder means that the relevant kernel module has not been loaded. In this case, the kernel module for the Savage card is not getting loaded at boot or when Xorg starts. That's why the GUI only works with the vesa driver. Checking with apt-cache shows that  xserver-xorg-video-savage is in fact installed. What I don't know is how to correct the discrepancy (Savage driver is installed but does not load or does not detect card) in Ubuntu.

---

### Post by Beeblebrx on 2013-10-14
Partially solved. The error was that savage.ko and savagefb.ko were not loaded. I had loaded both of them with modprobe, but did not realize that they would not be loading across reboots. Fixed by adding both modules into /etc/modules.

Now the problem is that the GUI screen is only partly visible. I suspect the problem is the wrong mode setting for the screen. /var/log/Xorg.0.log states: "Chose mode 117 at 60Hz". Any suggestions on how to find the best mode & refresh rate for the display?

Lastly, I have another laptop (similar specs) with same problem. The GPU on that one is a Trident Cyberblade/XP. The only kernel module that seems to exist for trident is video/tridentfb.ko; however loading that module does not create the /dev/dri/card0 link (the *fb modules are for the AGP function). There must be another kernel module laying around somewhere. Anyone know the name of the kernel module for Trident GPU's?

---

