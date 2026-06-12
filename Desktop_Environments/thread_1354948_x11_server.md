---
title: "x11 server"
date: 2009-12-14
forum: Desktop Environments
---

### Post by cybernet on 2009-12-14
i installed ati/amd drivers
see screenshot ( in the screenshot is already installed only is not activated for some reason ... )

after restarting my desktop looks fine ... but my windows moves like .... including scrooling 
how can i revert to the original setting 
* in /etc/x11/ there are no backup files
* dpkg-reconfigure xserver-xorg not working
( root@xList:/home/cybernet# dpkg-reconfigure xserver-xorg
root@xList:/home/cybernet# 
)

what do i do now ?:(
thanks in advance

---

### Post by cybernet on 2009-12-14
ooo come on :(

---

### Post by cybernet on 2009-12-15
nobody knows the answer :o

---

### Post by audiomick on 2009-12-15
could be that your problem is just that the driver isn't activated. You do that by clicking on the activate button in the bottom right of your screen shot.

---

### Post by wojox on 2009-12-15
You don't have a failsafe:

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

---

### Post by cybernet on 2009-12-15
> **audiomick said:**
> could be that your problem is just that the driver isn't activated. You do that by clicking on the activate button in the bottom right of your screen shot.

i forgot to mention that when i press activate the password box appears / after writing the password pres enter ... and nothin changes:(

in xorg.conf i have 
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

```

i'm guessing i will have to replace to the above code ...

---

### Post by cybernet on 2009-12-15
works perfectly
thanks a lot
and sorry fore being so impatient:D

---

### Post by aspiredfang on 2009-12-15
did you install the drivers from the ATI-***.run package or just let ubuntu handle it?

I had a similar problem when first switching to ubuntu but, using the the package from [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) fixed it for me. It is most likely the x config missing some lines. Other than the monitor stuff here is how mine looks after its auto-build and I have zero problems

```

Section "Module"
    Load  "dri"
    Load  "GLcore"
    Load    "glx"
EndSection

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "vesa"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    BusID       "PCI:1:0:0"
    Driver    "fglrx"
EndSection

```

---

