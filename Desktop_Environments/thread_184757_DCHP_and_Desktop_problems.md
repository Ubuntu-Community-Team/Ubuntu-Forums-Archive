---
title: "DCHP and Desktop problems"
date: 2006-05-30
forum: Desktop Environments
---

### Post by dunvar on 2006-05-30
I have recently installed Ubuntu 5.10 on 4 machines, get rid on Windows!  All machines but one are working and here is the low down.

Problems:

No Network
No Desktop

Symtoms:

Network:    eth0 not getting an I.P. from ADSL modem
Desktop:    Login comes up, but once use name and password entered, no desktop comes up, just the brown screen

Testing:

Network:    Connected ADSL modem to my personal laptop and was on the internet running Windows/Ubuntu 5.10
Network:    Tried Live CD to see if problems go away, same results.
Network:    Tried doing a reload and I get no I.P. Address with the DHCP with install disk
Network    Put in a new network card, both the Live and Install CD see both network cards and I selected eth1, but still am not getting I.P. Address


Desktop:    On the Desktop, removed GDM, went to apts cache and did a dpkg on the gdm deb file and reinstall GDM, still no desktop

Does anyone have any ideas?

---

### Post by jimbren on 2006-05-30
On the desktop, the only thing I can think to do would be to try and reinstall the complete desktop package.

```
sudo apt-get install ubuntu-desktop
```

You might also try installing Kubuntu, just so you have a GUI environment to work from.

```
sudo apt-get install kubuntu-desktop
```

---

### Post by dunvar on 2006-05-30
Ok, I'll try aptitude to uninstall that and then go to apt/cache and reinstall since I don't have networking to get to the internet.

---

### Post by waffen on 2006-05-30
[QUOTE=dunvar]Ok, I'll try aptitude to uninstall that and then go to apt/cache and reinstall since I don't have networking to get to the internet.[/QUOTE]

I have the same problem, see this: [http://ubuntuforums.org/showthread.php?t=180318]("http://ubuntuforums.org/showthread.php?t=180318")

---

