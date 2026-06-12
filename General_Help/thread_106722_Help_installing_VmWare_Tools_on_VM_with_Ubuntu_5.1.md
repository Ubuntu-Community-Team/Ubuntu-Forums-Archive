---
title: "Help installing VmWare Tools on VM with Ubuntu 5.10"
date: 2005-12-21
forum: General Help
---

### Post by XPiS on 2005-12-21
Ubuntu is installed as a guest OS on VmWare 5.5 final under Windows XP. Please help installing vmware tools, i tried installing with VMwareTools-5.5.0-18463.tar.gz but it required compiling kernel + modifying my gcc. This all thinks are rather complicated for me, so is there a .deb or smth else to help me in this problem?

---

### Post by adie273 on 2005-12-21
I could be wrong, i've never used VmWare. But if your using ubuntu on VmWare in WindowsXP. Wouldn't you need the Vmware tools for Windows rather than linux?

---

### Post by XPiS on 2005-12-21
"VMWare tools" is a program from vmware that is installed on a guest OS for better communication with host OS.

---

### Post by adie273 on 2005-12-21
Ahh, my bad. I figured it may be some kinda add-on for it.

I don't know of any .deb files for it, check VmWare website for some. If not you might not find any since VmWare is a commercial product. Its not free so doubt they'd like deb files of their product floating about the internet without their say so.

Adie

---

### Post by loupy on 2005-12-21
I actually run VMware in the reverse configuration as yours - but I think from the command line you need to do an:

export CC=/usr/bin/gcc-3.4

then run the vmware tools complile

---

### Post by XPiS on 2005-12-21
In the end I compiled the needed libs, etc. not too difficult, thanks to all.

---

