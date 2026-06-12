---
title: "System Crashes at Ubuntu Shutdown"
date: 2006-06-07
forum: Desktop Environments
---

### Post by Skychrono on 2006-06-07
Doing the normal shutdown procedure in X (not through the console), my screen goes all black with green dashes through it. I'll try to take a picture when I get home from work if someone would like...

I confirmed that it happens continuously - that is, I shut it down twice and it happened twice. Also, my video drivers work - at least, screensavers are nice and speedy.

This is from an eight-hours-fresh reinstall of Ubuntu 6.06. The only things I've installed are the things that Automatix installs (video drivers, some programs, etc). Oh, and Comix.

Any clue? I'm starting to wish that I had a STOP message to give you people...

Edit: System specs, if they'd help...

Athlon XP 1700+
GeForce 5900 (I've heard this is problematic...?)
SB Audigy
512 DDR RAM
40GB HD

---

### Post by tonyr on 2006-06-07
There are a couple of things to try before getting too complicated.

1. Look (edit) the file **/boot/grub/menu.lst**.  Find lines that begin with **kernel**.
    If the lines contain the word **splash**, you can remove the word by re-editting with
    root privileges.  If you are comfortable with command line use in a terminal, invoke your
    editor with **sudo**. Make a backup copy first,  I'm a **vi** guy, so I would say
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bck
sudo vi /boot/grub/menu.lst

```

If you are strictly UI, in Gnome you can ALT-F7 to get a run command window.
In KDE there is a **Run Command** entry in the **Kmenu**.


2. Edit the file **/etc/X11/xorg.conf**. Find the line that says **Section "Device"**. This
contains the video driver definition for your window server (X).  Mine looks like this:
```

Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 Go]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option         "NvAGP" "1"
EndSection

```

Yours will look vaguely similar, since you have an NVIDIA graphics controller.  What you
won't see is the line that says **Option "NvAGP" "1"**.  Editting that file with root
privileges as I described before, add that line.  Some people have success using the
value "0" instead of the value "1".  If neither of these work, post back here and we can
try other things.

---

### Post by tseliot on 2006-06-07
[QUOTE=tonyr]There are a couple of things to try before getting too complicated.

1. Look (edit) the file **/boot/grub/menu.lst**.  Find lines that begin with **kernel**.
    If the lines contain the word **splash**, you can remove the word by re-editting with
    root privileges.  If you are comfortable with command line use in a terminal, invoke your
    editor with **sudo**. Make a backup copy first,  I'm a **vi** guy, so I would say
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bck
sudo vi /boot/grub/menu.lst

```

If you are strictly UI, in Gnome you can ALT-F7 to get a run command window.
In KDE there is a **Run Command** entry in the **Kmenu**.


2. Edit the file **/etc/X11/xorg.conf**. Find the line that says **Section "Device"**. This
contains the video driver definition for your window server (X).  Mine looks like this:
```

Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 Go]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option         "NvAGP" "1"
EndSection

```

Yours will look vaguely similar, since you have an NVIDIA graphics controller.  What you
won't see is the line that says **Option "NvAGP" "1"**.  Editting that file with root
privileges as I described before, add that line.  Some people have success using the
value "0" instead of the value "1".  If neither of these work, post back here and we can
try other things.[/QUOTE]
I think he should try Point 1 and see if that solves the problem.

Then, if point 1 didn't solve the problem, he could try point 2.

---

### Post by Skychrono on 2006-06-07
[QUOTE=tonyr]2. Edit the file **/etc/X11/xorg.conf**. Find the line that says **Section "Device"**. This
contains the video driver definition for your window server (X).  Mine looks like this:
```

Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 Go]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option         "NvAGP" "1"
EndSection

```

Yours will look vaguely similar, since you have an NVIDIA graphics controller.  What you
won't see is the line that says **Option "NvAGP" "1"**.  Editting that file with root
privileges as I described before, add that line.  Some people have success using the
value "0" instead of the value "1".  If neither of these work, post back here and we can
try other things.[/QUOTE]

Thanks! Choice two helped (or... maybe choice one plus a required crash-y startup?).

Yay, features in Ubuntu. Thanks Tonyr + Automatix.

---

### Post by henok on 2008-04-25
Hi Everyone, I am still running into this problem and wanted to see if you can help me. I tried both of the suggestions from above but neither one worked. I put the word "splash" back into the kernel description because I notice all it did was disable the graphic boot. I am only having problems when shutting down. As soon as I click on shutdown, the screen begins to fade away, green lines appear all over the screen and then it shuts down.

I am on Sony Vaio VGN-S460, running Gutsy (7.10)

```

#-- /boot/grub/menu.lst

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ec1bab69-8d4d-4a4d-9787-bf0570d52848 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ec1bab69-8d4d-4a4d-9787-bf0570d52848 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

```

```

### /etc/X11/xorg.conf

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce Go 6200/6400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option "NvAGP" "1"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce Go 6200/6400]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

```

---

