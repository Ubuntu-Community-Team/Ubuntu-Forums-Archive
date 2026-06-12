---
title: "Gnome terminal rendering over all other windows"
date: 2011-10-24
forum: Desktop Environments
---

### Post by thePowersGang on 2011-10-24
I have a problem where gnome-terminal will be drawn over all other windows (and kept updated) but input events will be passed to the windows below. This includes the Alt-Tab window, gmrun and context menus, however the Unity-2D launcher still draws over the top.

I am running Unity-2D on Ubuntu 11.10 recently upgraded from 11.04, the machine is a Toshiba NB300.

As a note, the attached screenshot was taken of google-chrome using Alt-PrtSc, and still shows the terminal window, even though chrome had focus.

(As a note that may help, when I use Ubuntu Classic, the shadows render over menus, and the same behaviour shows. However, openbox does not, this seems to point to metacity being the problem)

---

### Post by thePowersGang on 2011-10-24
Of course, attachments do help

---

### Post by weatherhelm on 2011-10-24
I have this same problem just as described. I'm also running recently upgraded 11.10 in 2d.

---

### Post by AvalonSpirit on 2011-10-25
Have you checked if the always on top option is ticked for the terminal? I'm not sure in unity, but you should be able to right click on the window bar on top and select/unselect the always on top option.

If its set to default, i'm not sure how to change that, probably with the *gconf-editor*. 

If its something more complicated then I'm sure someone who knows more will soon be around.

---

### Post by thePowersGang on 2011-10-25
I have checked that, and it is not enabled. After unplugging my machine and taking it to Uni for the day, it appears that my Multi monitor setup causes/exposes the problem. As the terminal did not override anything while only the internal screen was in use.

Also, "2D Desktop Settings" shows that compositing is enabled (and the option is grayed out, so it cannot be disabled via that application). Maybe this is a problem with the video driver?

Details: 1024x600 internal screen, 1280x1024 VGA External, `lcpci` output for the display devices:
```

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller

```

---

### Post by weatherhelm on 2011-10-26
I confirmed that as well.

---

### Post by racinraz on 2011-11-04
same here. also only in dual monitor mode.

---

### Post by Lord Vetinari on 2011-11-07
Same thing here on dell optiplex 755 with dual display configuration and unity 2d (couldn't check this issue on 3d since my graphic card does not support dual display in 3d)
On gnome shell this issue does not occur.

lspci output:
```
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)


```Ubuntu 11.10 - all packages up to date

---

### Post by thotypous on 2011-11-13
Perhaps the problem happens because an Unity 2D session has Composite enabled by default in Ubuntu 11.10, whereas in Ubuntu 11.04 it didn't had.

I solved the problem by creating a /etc/X11/xorg.conf file containing:

```

Section "Extensions"
Option	 "Composite"	"Disable"
EndSection

```

---

### Post by akgrant on 2011-11-30
> **thotypous said:**
> Perhaps the problem happens because an Unity 2D session has Composite enabled by default in Ubuntu 11.10, whereas in Ubuntu 11.04 it didn't had.

I solved the problem by creating a /etc/X11/xorg.conf file containing: ...


Thanks for supplying this workaround.  Unfortunately it also disables the Unity 3d desktop.  I've had a look for a bug report but haven't found anything.  Does anyone know if one has been raised?

---

### Post by clanlaw on 2012-01-25
> **akgrant said:**
> Thanks for supplying this workaround.  Unfortunately it also disables the Unity 3d desktop.  I've had a look for a bug report but haven't found anything.  Does anyone know if one has been raised?

See [https://bugs.launchpad.net/unity-2d/+bug/788607](https://bugs.launchpad.net/unity-2d/+bug/788607)
Anyone seeing this issue please add themselves to this bug.

The easiest workaround, that does not affect unity 3d is to run
gconftool --set --type bool /apps/metacity/general/compositing_manager false
in a terminal.

---

