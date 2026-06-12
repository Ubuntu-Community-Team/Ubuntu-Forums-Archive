---
title: "Apple G5 iMac loves Etch 4.0r3!"
date: 2008-02-19
forum: Debian
---

### Post by stream303 on 2008-02-19
I've used Ubuntu PPC over the years and the forum support here for PPC has been great!  It made my install of Etch onto an early-model 20" G5 iMac a walk in the park.

So from an Ubuntu user's perspective, here's how Etch 4.0r3 went:

Anyone familiar with the "alternative" text-based installers usually recommended for Ubuntu PPC will be immediately familiar with Debian Etch installer.

At the boot prompt for my G5, I just typed "install64"

Followed the prompts for various questions, and dedicated the whole drive to Debian Etch when it came time to guided partitioning.  Walked away.

During install, the fans were totally quiet, unlike Ubuntu installers where the fans scream until you reboot.  Ah, blessed silence!

Debian updated me immediately during install, whereas in Ubuntu, you update afterwards.  Nice.

Upon reboot, the system worked just fine, although I did fix two problems based on my experience here in the Ubuntu forums.

(Although not a problem, I went into the font preferences and made sure that "subpixel smoothing" was chosen)

The machine ran at maximum cpu speed all the time, so all I had to do was install the "powernowd" daemon via synaptic. bingo.  Maybe not a problem, but a design consideration leaving it up to the user since this IS a desktop.

If I ran gparted, the machine would immediatly lose network connectivity and the system would run really slow.  Since I use a fixed ethernet cable from my router, I disabled the network manager (uninstalling it is not a good idea) as found in this invaluable Ubuntu wiki:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

Great - no network disconnects anymore when using gparted.

Browsing back into the Ubuntu forums with Iceweasel showed that the fonts were really ugly, even though they were fine everywhere else.  The fix - turn on dithering and autohinting, but say NO to using bitmapped fonts:  as root, enter

```
dpkg-reconfigure fontconfig-config
```

I also went into the fonts prefs again, and made sure that my DPI setting in the "details" tab was set to 99 or 100 for this 20" screen.  With this much screen real-estate, I changed most default sizes to about 12 or 13

[http://wiki.debian.org/iMacG5#head-40191678050a3a5c931c58af097e7f117ed29384](http://wiki.debian.org/iMacG5#head-40191678050a3a5c931c58af097e7f117ed29384)

The G5 has a very nice screen, and uses the "nv" video driver.  It is capable of an even better display by using FPDithering in xorg, so I just added:

```
Section "Device"
	Identifier	"nVidia Corporation NV34M [GeForce FX Go5200]"
	Driver		"nv"
	BusID		"PCI:240:16:0"
	[B]Option		"FPDither" "true"
[/B]EndSection
```

to my /etc/X11/xorg.conf file.

I found Debian Etch a totally rewarding experience, and although I'm not into the "us vs them" thing, and will continue to use Ubuntu AND Debian.  Even though there are other dedicated Debian forums, the Ubuntu PPC forum is a great community as well and want to thank them AND Debian.  Nice work everyone..

---

