---
title: "A few Kubuntu problems"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Asix on 2006-07-20
Hello all,
I've installed new Kubuntu 6.06 using LiveCD version, and everything works fine, except a few things...
First, when I open Adept Package Manager, there's not build - essential package listed, because I would like to install it so I can compile programs from scratch. I think it should be available in the list of packages without getting list from online repositories (it comes with Ubuntu CD, right?).
Next, when I open up Add/Remove Programs (Adept Installer), I can see software groups such as Graphics, Internet, Office, etc. but there's no Development section. As far as I know, there should be this section, where KDevelop is listed and some other development software. 
Is this normal because I've seen some 6.06 screenshots showing build - essential package in Adept by default after initial installation and a Development section in Adept Installer.
Did I do something wrong during the installation of the system or what?

---

### Post by aysiu on 2006-07-20
*build-essential* is on both the Desktop and Alternate CD, but it's not installed by default. ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
``` should do the trick.

Add/Remove is a simpler version of Adept. If you do ```
kdesu adept
``` you should see developer programs, too.

---

