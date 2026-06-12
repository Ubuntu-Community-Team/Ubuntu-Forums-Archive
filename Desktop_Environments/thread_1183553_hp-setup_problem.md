---
title: "hp-setup problem"
date: 2009-06-10
forum: Desktop Environments
---

### Post by Wim De Winter on 2009-06-10
Hi all,

I'm having trouble setting up my HP printer using hp-setup. I'm trying to do a fluxbox install on a minimal Ubuntu 8.04.2 LST. All's going well exept for the printer setup.

I've downloaded hplip-3.9.4b.run and started it doing

```
sh hplip-3.9.4b.run
```

All went well, until the setup process started. No printers could be detected, and I was advised to run hp-setup manually. I did just that, and a screen popped up. I selected the appropriate configuration being Parallel Port (LPT), and again, no printers were detected. I checked the "Hide Advanced Options" box, chose Manual Discovery and added /dev/parport0, the device to choose as seen in the result of 

```
lpinfo -v
```

It is stated there on line 4 that my printer, a DESKJET 610C, is on device /dev/parport0. But still no luck; hp-setup was unable to detect any printers. I've attached a screenprint to clarify things.

Or am I mistaken?

---

### Post by Wim De Winter on 2009-06-10
I'm still unable to do it gui-ways, but managed to install my printer by typing this:

```
hp-setup -i -a -x -d hp:/par/DESKJET_610C?device=/dev/parport0
```

I based this on the man pages found here: [http://hplipopensource.com/hplip-web/tech_docs/man_pages/setup.html]("http://hplipopensource.com/hplip-web/tech_docs/man_pages/setup.html")

---

