---
title: "Grub Killed my CDROM in Winblows Xp"
date: 2006-09-14
forum: Desktop Environments
---

### Post by Alvadore on 2006-09-14
I have been trying hard to get a duals boot system running with Ubuntu Dapper Drake on HD3 and Windows Xp on HD0,1.  I can get Ubuntu working just fine (well what did you expect?), but when I boot into windows the CDROM stops working during as soon as Windows begins to load.  Once lodaed and logged in, there is no CDROM at all.  Not even with a bang in device mangler.

Grub is installed on the mbr of the first HD.
Here's my Grub entry for Windows:
[B][COLOR="Blue"]title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1[/COLOR][/B]

Anyone have a suggestion or two?  I've been going nuts trying to figure this out and have dual booted the same system with Fedora, Suse and Gentoo but Ubuntu causes this every time.

---

