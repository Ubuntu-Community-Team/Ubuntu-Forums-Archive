---
title: "Wine"
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by jfox83 on 2007-06-03
I keep my software on a local hd. is it possible to map that drive to wine?

---

### Post by Ozzu on 2007-06-03
> **jfox83 said:**
> I keep my software on a local hd. is it possible to map that drive to wine?

Not sure if you're asking this question exactly, but it probably applies. From the Winehq.com FAQ:

[I]**Can I run applications directly off of a Windows installation without reinstalling them?**
Generally, no. Unless you know otherwise, you should leave your Windows installation alone and install things "fresh" into Wine. Most applications store their configuration data outside of their own folders, such as in the Windows registry. 

This isn't unique to Wine: you'll run into a similar problem under Windows itself if you try and run applications from another Windows installation. Wine (or the other Windows installation) has no way of seeing this data unless it was written into Wine's registry by the program installer. 

Some applications, however, are designed to be "portable" and don't use the registry at all, instead storing all of their settings in a file alongside the executable.[/I]

---

### Post by jfox83 on 2007-06-03
I keep the instalation instalation pacages there. this way my cd's do not get destroyed.

---

### Post by Prometheus.172214 on 2007-06-03
Firstly, having the installation files on the hard drive does not mean settings and configurations are also stored there. A program can be divided into components. The program's core files, the settings and saved files, the dependency files. A portable program is one which has all three components in the same place, which is true for a very small number of programs. Mostly these are small programs that have a very small size footprint. If you are looking into programs such as games, video editors and other large stuff, then I am sure the three components will be in different folders, different locations in the registry etc. So, loading these directly into Wine will firstly probably fail and also you will end up damaging the original files as well. Don't confuse your installation file dump on the hard drive (from the CD) with the installed files. Final say, let the Windows files stay the way they are and individually load your apps / programs into Wine, separately. Hope this helps....

---

### Post by cogadh on 2007-06-03
> **jfox83 said:**
> I keep the instalation instalation pacages there. this way my cd's do not get destroyed.

If you are saying that you copied the contents of the install CDs onto a drive in order to run the installation from there, yes, you can add that drive to Wine, but that doesn't guarantee that the installation will actually run if you try to install from that directory (some installation routines specifically look for the CD itself). Just run winecfg and manually add the drive on the "Drives" tab.

---

### Post by Ferrat on 2007-06-03
> **cogadh said:**
> If you are saying that you copied the contents of the install CDs onto a drive in order to run the installation from there, yes, you can add that drive to Wine, but that doesn't guarantee that the installation will actually run if you try to install from that directory (some installation routines specifically look for the CD itself). Just run winecfg and manually add the drive on the "Drives" tab.

wine can on the otherhand fake a CD altho no protections (like SecuROM and SafeDisk) but it can fake the label and the serialnr on a disc.

---

### Post by braddcadd on 2007-07-14
It worked very well.  Thunderbird, Firefox, & Sunbird all work through WINE.  I even got all my bookmarks, mail, ... on the thumb drive too.

Gaim does not work so well on WINE.  All I need through WINE in Sunbird.  This way I can keep one calendar.

---

