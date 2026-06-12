---
title: "Thunar Extract Here"
date: 2012-10-26
forum: Desktop Environments
---

### Post by Frogs Hair on 2012-10-26
Hi,

I am running the XFCE session on 12.10 and had been using Nautilus. A day ago I changed the default file manager to Thunar for this session and found it to be much faster in XFCE.

The problem is the Extract Here selection for packages doesn't open the packages. I have to use Extract To and re-select the directory I want to extract in before the file roller opens the package.

Due to inexperience with Thunar I don't know if this is normal or just because I am using the XFCE session and not the Xubuntu desktop. This is a minor inconvenience and any thoughts would be appreciated.

---

### Post by cmcanulty on 2012-10-26
I can use thunar and I do get the extract here rt cl option

---

### Post by Frogs Hair on 2012-10-26
Thanks, I will play around with the default applications for opening packages.

---

### Post by vasa1 on 2012-10-26
I remember reading that it is an "upstream" bug. I'll edit this post if I find a reference.

---

### Post by Frogs Hair on 2012-10-26
This may have been a glitch.I created a package archive and extracted it and then tested with a package I downloaded and now all is well.

---

### Post by LewisTM on 2012-10-26
There seems to be a bug with file-roller in 12.10.
On my machine, the extract-here operation makes the program crash. Never a good sign :C

An easy fix, which I just tested, is to uninstall file-roller and make sure **squeeze** is installed. Thunar - via its archive-plugin - will automatically detect that and use squeeze for it's archive operations.

Cheers!

---

### Post by Frogs Hair on 2012-10-26
Squeeze is installed and and extract is now working. Ill  see how it goes as I use Thunar more.

Thank You All.

---

### Post by PerLowgren on 2012-12-04
I replaced file-roller with squeeze and it worked until I had to extract a file-format unsupported by squeeze, so I found this alternative solution: [http://askubuntu.com/questions/52965/thunar-archive-plugin-not-working](http://askubuntu.com/questions/52965/thunar-archive-plugin-not-working)

Edit the file _gnome-file-roller.tap_ which on my machine is located here:[INDENT] /usr/lib/x86_64-linux-gnu/thunar-archive-plugin/gnome-file-roller.tap
[/INDENT]Replace:
```
file-roller "--extract-to=$(pwd)" --extract-here --force "$@"
```With:
```
file-roller --extract-here --force "$@"
```

---

### Post by MorningWood on 2012-12-06
> **PerLowgren said:**
> I replaced file-roller with squeeze and it worked until I had to extract a file-format unsupported by squeeze, so I found this alternative solution: [http://askubuntu.com/questions/52965/thunar-archive-plugin-not-working](http://askubuntu.com/questions/52965/thunar-archive-plugin-not-working)

Edit the file _gnome-file-roller.tap_ which on my machine is located here:[INDENT] /usr/lib/x86_64-linux-gnu/thunar-archive-plugin/gnome-file-roller.tap
[/INDENT]Replace:
```
file-roller "--extract-to=$(pwd)" --extract-here --force "$@"
```With:
```
file-roller --extract-here --force "$@"
```

Thank You PerLowgren, this worked beautifully.

---

### Post by pqwoerituytrueiwoq on 2012-12-06
the copy of file-roller in the proposed repo is fixed
look in the updates section of software sources

---

### Post by SantaFe on 2012-12-06
Yep, got the latest updates via Update Manager a couple of days ago & it mentioned File-Roller was one of them.  After updating, Thunar & PCmanFM both extract here just fine. ;)

---

