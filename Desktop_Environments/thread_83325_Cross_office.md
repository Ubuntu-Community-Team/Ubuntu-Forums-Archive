---
title: "Cross office?"
date: 2005-10-28
forum: Desktop Environments
---

### Post by Sunnz on 2005-10-28
Can someone tell me, what exactly is Cross Office? I have been to the site but their description is very confusing.

---

### Post by N6546R on 2005-10-28
Crossover Office is a program that allows you to run certain Microsoft Windows programs under Linux. For example, you can launch Internet Explorer or Microsoft Word.

Not all Windows programs work with Crossover Office, and the ones that do often require a specific version.

Perry

---

### Post by Sunnz on 2005-10-29
So it is like Wine then? But the site says it support Wine, which implies it is not like Wine...

---

### Post by jasay on 2005-10-29
Crossover office is, I think, a fork of wine that's geared toward business people.  It's basically wine with a pretty gui for installing windows programs (mostly business/office stuff) and more technical support for said programs.  It takes care of some of the configuration so more programs work 'out of the box' than wine, but nothing is guaranteed unless it's on the list of supported software.  Cedegra is a similar fork but focuses on games/directx instead of office software.

---

### Post by Sunnz on 2005-11-06
So... on cross office you just double click the Windows Installer and it will install the software on correct directory? (/opt/blah?)

---

### Post by jasay on 2005-11-06
That sometimes works, but I think double clicking uses a set of generic preferences that don't work for all programs.  For the best chance of success you actually open Crossover Office and select what you are trying to install from a list.  It then sets everything up optimally for that particular program/version.  It installs the programs in a hidden file in your home directory (although if you run as root it might go somewhere else so all users can run the program???)

---

### Post by GrumpyBob on 2005-11-06
I have a Hoary box with Crossover Office 4.2 on it.  It's been very useful for those Windows apps I've needed to use (mostly MS Office).  I find I'm needing these apps less and less nowadays.

Crossover Office seems a very nice and easy to use fork of Wine.  They offer a trial version, so at least you can see if it will perform OK with the apps you want to use.

I've also used Wn4Lin, and tried qemu, with varying levels of success.  The old Win4Lin required a specially compiled kernel, which is a pest - I believe newer versions are based on qemu or similar.

Robert

---

### Post by Sunnz on 2005-11-06
That's still rather confusing... the Windows installer would assume something like C:\program files right? A list of apps from within cross office? So they actually port some of the Windows native programs into their product?

---

### Post by manicka on 2005-11-06
No, wine or crossover office emulates windows so that you can install the native windows program on it. Crossover sets up a fake c drive in your home directory that the windows programs are installed to.

You install programs in a slightly different way in that you use the nice crossover control panel to initiate the installer. After that though it's pretty much just like using the program in windows. Crossover installs icons into your menus and away you go

---

### Post by Sunnz on 2005-11-06
Oh ok, so I would need to original CD and stuff right? Maybe I'll try it out.

---

### Post by manicka on 2005-11-06
[QUOTE=Sunnz]Oh ok, so I would need to original CD and stuff right? Maybe I'll try it out.[/QUOTE]

Not for Windows, just the programs

---

