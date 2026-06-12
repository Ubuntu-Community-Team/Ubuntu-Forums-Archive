---
title: "Gnome, KDE, Xfce on one comp...Problem"
date: 2006-10-25
forum: Desktop Environments
---

### Post by macogw on 2006-10-25
I'm trying to install Xfce.  I already have Gnome and KDE.  There's a problem though.  

```
mack@mack-laptop:~$ sudo apt-get install xubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
xubuntu-desktop is already the newest version.
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  xubuntu-desktop: Depends: xfce4-terminal but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).

```
And if I follow those directions:
```
sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  xfce4-terminal
The following NEW packages will be installed
  xfce4-terminal
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/998kB of archives.
After unpacking 2802kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 158762 files and directories currently installed.)
Unpacking xfce4-terminal (from .../xfce4-terminal_0.2.5+r21674-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xfce4-terminal_0.2.5+r21674-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/bin/Terminal', which is also in package terminal.app
Errors were encountered while processing:
 /var/cache/apt/archives/xfce4-terminal_0.2.5+r21674-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
How do I get whatever dependency is causing the problem?

---

### Post by kerry_s on 2006-10-25
sudo rm /usr/bin/Terminal

---

### Post by tigerstripedcat on 2006-10-25
I wouldn't just rm it, You should try and find the package that has that file, maybe use auto-apt, and then remove that pacackage, not the file.

---

### Post by macogw on 2006-10-25
How do I do that? sudo auto-apt /usr/bin/Terminal ?

---

### Post by kerry_s on 2006-10-25
> **tigerstripedcat said:**
> I wouldn't just rm it, You should try and find the package that has that file, maybe use auto-apt, and then remove that pacackage, not the file.

It should replace it with the same app. But he could just rename it to Terminal.bak and it sholud also work.

---

### Post by macogw on 2006-10-26
> **kerry_s said:**
> It should replace it with the same app. But he could just rename it to Terminal.bak and it sholud also work.
Which means, what?  I go into that folder and rename the Terminal then download the last package?


*she

---

### Post by macogw on 2006-10-26
I can't rename it.  Rename is greyed out.

---

