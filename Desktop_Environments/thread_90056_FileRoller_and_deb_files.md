---
title: "FileRoller and deb files"
date: 2005-11-14
forum: Desktop Environments
---

### Post by Kray on 2005-11-14
I just installed Breezy and discovered that FileRoller is unable to open deb files ('Unsupported archive type' message or smth like that). I've installed all suggested packages for FileRoller via Synaptic, but without results.

I'm pretty sure that in Hoary FileRoller had support for deb files out-of-box. So what is wrong now?

---

### Post by Kyral on 2005-11-14
There is a very good reason for this.

Deb files are not archives in the way that tar.gz, tar.bz2, tgz, etc etc etc are. They are better known as Debian Packages or Debpacks for short. They are most equivelent to the .exe in Windows (RPMs are the same way) in that they install things on your system.

How do you install these things, quite simple my good person! Crack open a Terminal and cd to the directory where you downloaded it. Then ```
sudo dpkg -i <nameoffile>
```

---

### Post by ranf on 2005-11-14
[QUOTE=Kray]I just installed Breezy and discovered that FileRoller is unable to open deb files ('Unsupported archive type' message or smth like that). I've installed all suggested packages for FileRoller via Synaptic, but without results.

I'm pretty sure that in Hoary FileRoller had support for deb files out-of-box. So what is wrong now?[/QUOTE]
On my box (Breezy) file-roller opens .deb's.

$ file-roller --version
Gnome file-roller 2.12.1

---

### Post by ranf on 2005-11-14
[QUOTE=Kyral]
Deb files are not archives in the way that tar.gz, tar.bz2, tgz, etc etc etc are. [/QUOTE]
They are packed with `ar' and contain a text file and two .tar.gz.

---

### Post by Kyral on 2005-11-14
Oh. Didn't know that (Kinda feel stupid since I make Debpacks)

---

### Post by ranf on 2005-11-14
Never mind. :-)

---

### Post by Kray on 2005-11-15
Kyral:

I know what are DEB files and how to install them ;-). I just want to view content of one package :p

ranf:

I've got same version of FileRoller. Probably u have installed some package which adds support for DEB format to FileRoller (just like rar or arj packages). Do u have any idea which package it is?

Greetings, Kray

---

### Post by ranf on 2005-11-15
[QUOTE=Kray]
I've got same version of FileRoller. Probably u have installed some package which adds support for DEB format to FileRoller (just like rar or arj packages). Do u have any idea which package it is?
[/QUOTE]
In file-roller when I choose Archive -> New I can see a list of filetypes:
[LIST]
[*]ar
[*]ear
[*]jar
[*]tar
[*]tar.bz2
[*]tar.gz
[*]tar.lzo
[*]war
[*]zip
[/LIST]

`ar' is in package `binutils'.

---

### Post by Kray on 2005-11-15
Thx a lot :-).

---

### Post by abou on 2005-11-15
Since we are on the topic of FileRoller, is there any way for it to act as a frontend for p7zip?  Command line is okay, but frontends spoil me.

---

