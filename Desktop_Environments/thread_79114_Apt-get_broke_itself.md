---
title: "Apt-get broke itself"
date: 2005-10-19
forum: Desktop Environments
---

### Post by argosreality on 2005-10-19
When Breezy first came out I had to run "sudo apt-get update/dist-upgrade" a total of three times for my system to actually come up to date. Afterwards, I noticed that quite a few packages were held back even though newer versions are out there. Of course, me being silly I thought I'd force them. MPlayer upgraded fine to the latest version, <i>however</i> Muine has not played so nice. In fact, its now broken my apt-get.

Here's what I get when I attempt to upgrade (or install anything)
```
chris@skylar:/usr/lib$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  muine-plugin-trayicon: Depends: libglib2.0-cil (>= 2.3.90) but 1.9.5-0ubuntu1~5.04ubp1 is installed
                         Depends: libgtk2.0-cil (>= 2.3.90) but 1.9.5-0ubuntu1~5.04ubp1 is installed
E: Unmet dependencies. Try using -f.

```
Ok, so now I try doing "sudo apt-get -f install":
```
chris@skylar:/usr/lib$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgconf2.0-cil libglade2.0-cil libglib2.0-cil libgnome2.0-cil libgtk2.0-cil
  muine
The following packages will be REMOVED:
  muine-dbus muine-plugin
The following packages will be upgraded:
  libgconf2.0-cil libglade2.0-cil libglib2.0-cil libgnome2.0-cil libgtk2.0-cil
  muine
6 upgraded, 0 newly installed, 2 to remove and 41 not upgraded.
1 not fully installed or removed.
Need to get 0B/1483kB of archives.
After unpacking 668kB disk space will be freed.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 126075 files and directories currently installed.)
Preparing to replace muine 0.8.3-3ubuntu1~5.04ubp1 (using .../muine_0.8.3-5ubuntu7_i386.deb) ...
Unpacking replacement muine ...
dpkg: error processing /var/cache/apt/archives/muine_0.8.3-5ubuntu7_i386.deb (--unpack):
 trying to overwrite `/usr/lib/mono/gac/muine-dbus/1.0.0.0__e6bf890338fa2913/muine-dbus.dll', which is also in package muine-dbus
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/muine_0.8.3-5ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Finally, getting frustrated with it I just try and remove Muine (not that I use it regularly) and say the hell with it. Sadly, apt-get doesn't like that:
```

chris@skylar:/usr/lib$ sudo apt-get remove muine
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  muine-plugin-trayicon: Depends: libglib2.0-cil (>= 2.3.90) but 1.9.5-0ubuntu1~5.04ubp1 is to be installed
                         Depends: libgtk2.0-cil (>= 2.3.90) but 1.9.5-0ubuntu1~5.04ubp1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
I'm at a loss. I can't install, remove, or update ANYTHING anymore. Anyone have any ideas? Please? :)

**EDIT: Forgot to mention I'm running Breezy 5.10 though I also have Kubuntu installed as well.

---

### Post by invalid on 2005-10-19
Try
```
sudo apt-get remove muine-dbus
```

Cheers,
Cb

---

### Post by argosreality on 2005-10-19
[QUOTE=invalid]Try
```
sudo apt-get remove muine-dbus
```

Cheers,
Cb[/QUOTE]Still no go. Causes the same error as doing "apt-get remove muine." Thanks for the try tho

---

### Post by Ampersand on 2005-10-19
What about
```
sudo apt-get remove muine muine-dbus muine-plugin-trayicon
```

---

### Post by argosreality on 2005-10-19
[QUOTE=Ampersand]What about
```
sudo apt-get remove muine muine-dbus muine-plugin-trayicon
```[/QUOTE]Ah! I totally forgot about chaining them all. Anyways, it worked perfectly! Thank ya very much :)

---

