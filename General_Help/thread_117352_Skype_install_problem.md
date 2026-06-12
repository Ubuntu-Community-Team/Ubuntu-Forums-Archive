---
title: "Skype install problem"
date: 2006-01-14
forum: General Help
---

### Post by Red Knuckles on 2006-01-14
When I try to install the Debian package for Skype I get:

zzzzz@c-xxx-xxx-xxx-xxx:~$ sudo dpkg -i skype.deb
Selecting previously deselected package skype.
(Reading database ... 73717 files and directories currently installed.)
Unpacking skype (from skype.deb) ...
dpkg: dependency problems prevent configuration of skype:
skype depends on libqt3c102-mt (>= 3:3.3.3.2); however:
 Package  is not installed.
dpkg: error processing skype (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
skype

How can I fix this? When I try to Install 'libqt3c102-mt' I get:

:~$ sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate

The 'libqt3-mt' package is installed:

:~$ sudo apt-get install libqt3-mt
Reading package lists... Done
Building dependency tree... Done
libqt3-mt is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

What I gonna do about this???:confused: Things just don't seem quite right with Skype for linux!!!:rolleyes:

---

### Post by mztriz on 2006-01-14
I know there is a thread on this website somewhere about this, I used it my self to install skype (I'm looking for it right now).

---

### Post by mztriz on 2006-01-14
okay, I found it.
[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)

---

### Post by Red Knuckles on 2006-01-14
[QUOTE=mztriz]okay, I found it.
[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)[/QUOTE]

Thank you.:)

---

### Post by KhanArash on 2006-01-14
[QUOTE=Red Knuckles]Thank you.:)[/QUOTE]

Did u make it to work? I have installed it and I am waiting for about 10 minuttes and its not started yet!:confused:

---

### Post by Red Knuckles on 2006-01-14
[QUOTE=KhanArash]Did u make it to work? I have installed it and I am waiting for about 10 minuttes and its not started yet!:confused:[/QUOTE]

The .deb version does not work in Ubuntu to my knowledge. I downloaded the tar.bz2 version:

Static binary tar.bz2 with Qt 3.2 compiled in (10.4 MB)

and I have Skype up and working fine so far.:)

---

### Post by Red Knuckles on 2006-01-14
[QUOTE=KhanArash]Did u make it to work? I have installed it and I am waiting for about 10 minuttes and its not started yet!:confused:[/QUOTE]

Another way is to install the Fedora Core 3 version as described in this link:

[https://wiki.ubuntu.com/SkypeHowto?highlight=%28Skype%29](https://wiki.ubuntu.com/SkypeHowto?highlight=%28Skype%29)

:smile:

Hope one of these 2 methods works for you. Let us know what did work!

---

### Post by KhanArash on 2006-01-14
[QUOTE=Red Knuckles]Another way is to install the Fedora Core 3 version as described in this link:

[https://wiki.ubuntu.com/SkypeHowto?highlight=%28Skype%29](https://wiki.ubuntu.com/SkypeHowto?highlight=%28Skype%29)

:smile:

Hope one of these 2 methods works for you. Let us know what did work![/QUOTE]

To start Skype, choose Applications->Internet->Skype. It usually takes a minute or two for Skype to get started, and you will think that nothing is happening, so be patient.

I have been waiting for more than 10 minuttes now:confused:

---

### Post by whiteB on 2006-07-31
Use UBUNTU 6 and Skype 1.3 beta RPM...And convert it to
 .deb and use... Will get fantastic results...

---

### Post by darden68 on 2006-07-31
worked well for me. I got it from here : [http://skype.com/download/skype/linux/13beta.html](http://skype.com/download/skype/linux/13beta.html)

---

