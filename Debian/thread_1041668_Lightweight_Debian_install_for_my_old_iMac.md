---
title: "Lightweight Debian install for my old iMac"
date: 2009-01-16
forum: Debian
---

### Post by spencercarran on 2009-01-16
I've got an ancient iMac G3 (400MHz PPC, 320MB RAM) that I want to squeeze some more use out of. My plan is to install Debian with IceWM on it. I'm sure it would run XFCE just fine, but I'd rather use IceWM and get the extra performance. My question is... well, this is kind of awkward. I don't exactly know where to start- the Debian site has like a bajillion different ISO's to download, and I'm not sure which to get. Is the netinst the correct one? And then I would get a minimal Debian install by running the installer off of that, and (as root) "aptitude install xorg gdm icewm" correct? And then "startx" to get it started after leaving root? Would it then go straight to GDM on booting rather than a command prompt? This is something that's intended to stay at home for my family, who've never used Linux, so ideally I'd find a way to get a simple log-in without the big scary command-line.:P

I tried a similar process from an ubuntu-minimal install and got nothing. From the base install, I added "sudo aptitude install xorg xterm gdm icewm" and got absolutely nothing after entering "startx." My screen just went blank.

Any help would be greatly appreciated. I've never used Debian before, and am fairly new to Linux in general (having only seriously used Ubuntu thus far).

---

### Post by kerry_s on 2009-01-16
you should try lxde, grab the new light iso:
[http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/debian-testing-powerpc-xfce+lxde-CD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/debian-testing-powerpc-xfce+lxde-CD-1.iso)

the iso offers a choice between xfce4 or lxde.
choose lxde, its way lighter than anything else desktop wise.

---

### Post by spencercarran on 2009-01-16
I'm not a huge LXDE fan (tried it briefly in a half-baked Sabayon). I'll give it a try when/if I fail at setting up IceWM, though, so thanks for the link.

---

### Post by RedSquirrel on 2009-01-16
> **spencercarran said:**
> I don't exactly know where to start- the Debian site has like a bajillion different ISO's to download, and I'm not sure which to get. Is the netinst the correct one? 

I like the business-card iso. It's a bit smaller and works well as long as you have a decent internet connection.

edit: When you get to the step in the installer that asks which software sets you want, make sure you un-check the "Desktop system" option since that will install GNOME etc.



> **spencercarran said:**
> And then I would get a minimal Debian install by running the installer off of that, and (as root) "aptitude install xorg gdm icewm" correct? And then "startx" to get it started after leaving root? Would it then go straight to GDM on booting rather than a command prompt?

You might have to setup a basic /etc/X11/xorg.conf file. 

In some cases, it is possible to not have one and X will work just fine. There may be a default xorg.conf under /etc/X11 that works, or you can generate a basic xorg.conf by running (as root):

```
dpkg-reconfigure xserver-xorg
```You could go ahead and try running startx (as your regular user) to see if icewm appears. When you install icewm, it should automatically be the default window manager that gets started when you run startx.

Note: startx will not load gdm; there is a different way to load that from the command line (as root):

```
/etc/init.d/gdm start
```Alternatively, you could just reboot (press Ctrl-Alt-Delete). When the computer finishes booting, you should be at the gdm login screen (**as long as Xorg is configured correctly** -- probably best to test things first by running startx as described above).

---

### Post by spencercarran on 2009-01-16
> **RedSquirrel said:**
> You might have to setup a basic /etc/X11/xorg.conf file. 

In some cases, it is possible to not have one and X will work just fine. There may be a default xorg.conf under /etc/X11 that works, or you can generate a basic xorg.conf by running (as root):

```
dpkg-reconfigure xserver-xorg
```You could go ahead and try running startx (as your regular user) to see if icewm appears. When you install icewm, it should automatically be the default window manager that gets started when you run startx.
Running ```
dpkg-reconfigure xserver-xorg
``` asks me for the video bus id. How do I find that? When I enter "lspci" as recommended by xserver-xorg config, I get ```
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
0000:00:10.0 Display Controller: ATI Technologies Inc Rage 128 RL/VR AGP
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth PCI
0001:10:12.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 02)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth Internal PCI
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM)
```

---

### Post by spencercarran on 2009-01-17
OK, after some digging around I figured out the correct BusID. (figuring out that I was supposed to convert from hexadecimal to decimal took a while)

Now "startx" fails and gives me the error message ```
(EE) No drivers available.

Fatal server error:
no screens found

waiting for X server to begin accepting connections
giving up.
```

---

### Post by RedSquirrel on 2009-01-17
Your graphics hardware uses the driver found in the **xserver-xorg-video-ati** package. That should have been installed automatically when you installed the **xorg** package, so it could be that your current /etc/X11/xorg.conf has some incorrect settings.

I would see what sort of /etc/X11/xorg.conf you get from running (as root):

```
dpkg-reconfigure -phigh xserver-xorg
```If it's different from the one you generated before, see what happens when you run startx.

If that doesn't help, I would try (as root):

```
X -configure
```This will generate the file /root/xorg.conf.new.

Copy it over to the /etc/X11 directory:

```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```and then try startx again.

---

### Post by spencercarran on 2009-01-17
> **RedSquirrel said:**
> Your graphics hardware uses the driver found in the **xserver-xorg-video-ati** package. That should have been installed automatically when you installed the **xorg** package, so it could be that your current /etc/X11/xorg.conf has some incorrect settings.

I would see what sort of /etc/X11/xorg.conf you get from running (as root):

```
dpkg-reconfigure -phigh xserver-xorg
```If it's different from the one you generated before, see what happens when you run startx.
I get ```
(WW) R128: No matching device for instance (BusID PCI:0:16:0) found
(EE) No Devices detected.

Fatal server error:
no screens found
```

> ```
X -configure
```This will generate the file /root/xorg.conf.new.

Copy it over to the /etc/X11 directory:

```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```and then try startx again.
That makes the error messages stranger. I get a blank screen, and killing X displays a bunch of repeated "(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument:
Then > (II) Module "ramdac" already built-in
Could not init front path element /usr/shar/fonts/X11/cyrillic, removing from list!
could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirss/TrueType, removing from list!
[config.hal] couldn't initialize contextL (null) ((null))
xinit: connection to X server lost.

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

---

### Post by RedSquirrel on 2009-01-17
> **spencercarran said:**
> That makes the error messages stranger. I get a blank screen, and killing X displays a bunch of repeated "(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument:
Then

Interesting. I haven't encountered these errors before. Getting old hardware to work sometimes requires a bit of tinkering. If you haven't done so already, Google the error "FBIOPUT_VSCREENINFO: Invalid argument" and see what you can find.

I had a quick look around and saw that dropping the bit depth to 16 might help.

```
Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth 16
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    .
    .
    .

```

[This]("http://forums.debian.net/viewtopic.php?p=201778&sid=8dfad8cfd0b1796ea2a443d35d2081be") thread might be of some help as well.

---

### Post by polmir on 2009-01-17
Try this script:
[http://techpatterns.com/forums/about933.html]("http://techpatterns.com/forums/about933.html")

---

### Post by Muldarfbi on 2009-01-17
I am running Ubuntu 8.10 Intrepid Ibex 64bit...
I also have Debian 3.1 Sarge (stable).
I have the whole disc set of Debian 3.1, (19 disc)
Can I use the Debian packages on Ubuntu 8.10?

Thanks in advance for the help...
Muldarfbi,

---

### Post by oswaldkelso on 2009-01-18
How to install debian on imac-emac ppc, very verbose set-up
[http://forums.debian.net/viewtopic.php?t=20481&](http://forums.debian.net/viewtopic.php?t=20481&)

Blank screen on iMac G3 with Debian Lenny
[http://www.my2bits.org/?p=72](http://www.my2bits.org/?p=72)

(2.6.28 kernels) .debs with or without altivec depending on your model

Running kernel-libre on ppc
[http://www.my2bits.org/?p=76](http://www.my2bits.org/?p=76)
pics
[http://www.my2bits.org/?p=57](http://www.my2bits.org/?p=57)

info [www.ppclinux.info](www.ppclinux.info)

---

### Post by oswaldkelso on 2009-01-18
> **Muldarfbi said:**
> I am running Ubuntu 8.10 Intrepid Ibex 64bit...
I also have Debian 3.1 Sarge (stable).
I have the whole disc set of Debian 3.1, (19 disc)
Can I use the Debian packages on Ubuntu 8.10?

Thanks in advance for the help...
Muldarfbi,

If I was to give a one word answer. No. Sarge is way to old to try mixing with ibex.

---

### Post by CREEPING DEATH on 2009-01-31
I wonder if it isn't the same issue that comes up with OSX installations on G3 iMacs?  Needs a firmware upgrade?

CD

---

