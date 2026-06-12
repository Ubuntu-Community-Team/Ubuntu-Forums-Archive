---
title: "nvidia TVout"
date: 2004-10-18
forum: General Help
---

### Post by Rancoras on 2004-10-18
I'm trying to get TVout working easily with my machine.  When I first tried ubuntu back with the preview release of warty, this process worked fine.  Shortly after that I had a hard drive crash on this machine and have since reinstalled warty.  Everything is the same on this machine except the hard drive.  I'm just now getting around to putting the TVout back to rights.

I added or modified these three sections in my default X config:

```
Section &quot;Monitor&quot;
	Identifier  &quot;TV&quot;
	HorizSync 30-50
	VertRefresh 60
EndSection
Section &quot;Screen&quot;
	Identifier  &quot;tvout800&quot;
	Device      &quot;NVIDIA Corporation NV34 &#91;GeForce FX 5200&#93;&quot;
	Monitor     &quot;TV&quot;
	DefaultDepth 24
	Option &quot;TVStandard&quot; &quot;NTSC-M&quot;
	Option &quot;ConnectedMonitor&quot; &quot;TV&quot;
	Subsection &quot;Display&quot;
		Depth       24
		Modes       &quot;800x600&quot;
		ViewPort    0 0
	EndSubsection
EndSection

Section &quot;ServerLayout&quot;
	Identifier	&quot;Default Layout&quot;
	#Monitor
	Screen		&quot;Default Screen&quot;
	#TV
	#Screen		&quot;tvout800&quot;
	InputDevice	&quot;Generic Keyboard&quot;
	InputDevice	&quot;Configured Mouse&quot;
EndSection
```

What I want is to be able to launch a new X server on VT8 that will show up on the TV for watching videos, etc.  I can then switch between the servers with CTRL+ALT+F7 / F8.  Then when the new server is killed, all goes back to normal.  For that I am using this command:

```
sudo startx $* -- &#58;1 -depth 24 -screen tvout800 
```

In my first install, this worked fine, the X server launched on the TV and I got my regular GDM login screen.  Now, the server launches on the TV but stays at the "stippled gray" screen with the "x" cursor.  GDM doesn't launch.  I'm not sure what has changed and when it changed.  Can anyone help?

---

### Post by Rancoras on 2004-11-02
I had forgotten about this one.  Anyone got any ideas now?  Consider this a *bump* :)

---

### Post by snellgrove on 2004-11-12
Im a bit of a linux n00b so dont really know how to help, other than is there any logs or anything to view?

maybe theres a way to see what the error is?  

I dunno though..  :oops:

---

### Post by Rancoras on 2004-11-12
There's no error, it just doesn't work like it did in the preview release.

---

### Post by ljoris on 2004-11-15
[QUOTE=Rancoras]There's no error, it just doesn't work like it did in the preview release.[/QUOTE]

Just check out the nvidia website, your XF86Config and all you need to modify it is to be found there, FAIK it's in /usr/share/doc/...

---

### Post by piedamaro on 2004-11-17
[QUOTE=Rancoras] Now, the server launches on the TV but stays at the "stippled gray" screen with the "x" cursor.  GDM doesn't launch.  I'm not sure what has changed and when it changed.  Can anyone help?[/QUOTE]

Why gdm should launch? AFAIK startx executes .xinitrc file, which should be filled with the commands you want to launch.
Usually I login with another user, then I issue startx -- :1, so I guess your command should work to. Btw, why is there a $* in front of startx? (maybe you use it in another script). I'm confused: a static stippled grey screen is weird, it should either exit immediately, or load your startup programs. 
 :???:

---

### Post by ynef on 2004-11-18
Yeah, what piedamaro said -- try to add at least and xterm to your .xinitrc file to see if that comes up on the TV. If you can get an image of any kind then you know that the setup is basically correct.

---

### Post by p!=f on 2004-11-18
This is the part of my old but still working XF86Config-4. It may help you get things up and then tweak it to make it work with the second xserver as you wish.
```

Section "Device"
        Identifier      "nVidia GeForce4 MX"
        Driver          "nvidia"
        Option          "NvAGP"                 "1"
        Option          "RenderAccel"           "1"
        Option          "HWCursor"              "1"
        Option          "CursorShadow"          "1"
        Option          "UseFBDev"              "1"
        #Option         "TwinView"              "1"
        #Option         "MetaModes"             "1152x864, 640x480"
        #Option         "SecondMonitorHorizSync"        "30-50"
        #Option         "SecondMonitorVertRefresh"      "60"
        #Option         "TwinViewOrientation"   "Clone"
        #Option         "ConnectedMonitor"      "CRT, TV"
        #Option         "TVStandard"            "PAL-B"
        #Option         "TVOutFormat"           "SVIDEO"
EndSection

```

If 5200 has a TV chip (too lazy to browse the net now :)), you might want to take a look at *nvtv* package.
```

 * 15:04:22 * pef @ agonicus *
[~] > wajig show nvtv
Package: nvtv
Priority: optional
Section: universe/admin
Installed-Size: 1056
Maintainer: Roberto Lumbreras <rover@debian.org>
Architecture: i386
Version: 0.4.7-1
Provides: tvtool
Depends: libatk1.0-0 (>= 1.6.0), libc6 (>= 2.3.2.ds1-4), libglib2.0-0 (>= 2.4.1), libgtk2.0-0 (>= 2.4.4), libice6 | xlibs (>> 4.1.0), libpango1.0-0 (>= 1.5.2), libsm6 | xlibs (>> 4.1.0), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), libxmu6 | xlibs (>> 4.1.0), pciutils (>= 1:2.1.11-11)
Filename: pool/universe/n/nvtv/nvtv_0.4.7-1_i386.deb
Size: 284992
MD5sum: 4a0af66f6503984dedde99a39e5434c7
Description: Tool to control TV chips on NVidia cards under Linux
 This is a program to control the TV encoder chips on NVidia cards under
 Linux, in order to get tv-out with a wide range of resolutions and
 sizes, including "overscan" modes. It does even work with the free nv drivers.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

What nVidia drivers you use?

---

