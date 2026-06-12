---
title: "Error when installing movie-making software"
date: 2011-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RSASKA on 2011-05-08
Hello,

To help with studying for certifications (required for job), I would like to make movies similar to [www.xtranormal.com]("http://www.xtranormal.com").

They have software (StatePackage.exe), where you can download and create your own movies by typing.

I downloaded and installed WIne.

I downloaded StatePackage.exe, it unzips to C:\windows\temp, then  the following error pops up:



Runtime Error!

Program C:\windows\temp\Setup.exe

R6034
An application has made an attempt to load the C runtime library incorrectly.


How do I resolve this?


More Information:

I attempted to open a Terminal

Went to [USER]@dell-desktop:~/.wine/drive_c where StatePackage.exe is located

Typed in the command sudo StatePackage.exe

Prompted me for my Administrator password

Received, "sudo: StatePackage.exe: command not found"

---

### Post by RedRat on 2011-05-08
> **RSASKA said:**
> Hello,

To help with studying for certifications (required for job), I would like to make movies similar to [www.xtranormal.com]("http://www.xtranormal.com").

They have software (StatePackage.exe), where you can download and create your own movies by typing.

I downloaded and installed WIne.

I downloaded StatePackage.exe, it unzips to C:\windows\temp, then  the following error pops up:



Runtime Error!

Program C:\windows\temp\Setup.exe

R6034
An application has made an attempt to load the C runtime library incorrectly.


How do I resolve this?


More Information:

I attempted to open a Terminal

Went to [USER]@dell-desktop:~/.wine/drive_c where StatePackage.exe is located

Typed in the command sudo StatePackage.exe

Prompted me for my Administrator password

Received, "sudo: StatePackage.exe: command not found"
There is a Wine web page that lists the various required DLLs that can be downloaded and installed to make certain windows programs work. Can't remember the site right now. Check out the Wine web page.

---

### Post by RSASKA on 2011-05-09
I went to 

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

And attempted to follow the directions to install latest version of Wine (I have 1.0.1)

However, when I go to 

*System > Administration > Software Sources > Third-Party Software > Add*

And copy and paste

[I]ppa:ubuntu-wine/ppa

[/I]The +Add Source button is disabledPlease note I have Ubuntu 9.04

---

