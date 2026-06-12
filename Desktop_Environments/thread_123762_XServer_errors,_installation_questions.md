---
title: "XServer errors, installation questions"
date: 2006-01-30
forum: Desktop Environments
---

### Post by Taigrr on 2006-01-30
Okay, this might be long, so please please stick with it, I would be most appreciative, being very new to Linux, let alone Ubuntu.

I installed Ubuntu on an old computer, Pentium 2, 266, and it worked fine. I got in, games worked, office stuff worked, firefox, gaim. It all worked perfect. Then I tried to put the HD into a server box, that has no CDROM or Floppy. Obviously, there were some comflics hardware wise. But the only one it came up with, was that the XServer wasn't configured right. So I tried sudo dpkg-reconfig xserver-xorg, and went through it all, and it didn't help. did I do something wrong, or is there an auto-configure?

If that doesn't matter, then I am just going to uninstall and reinstall on the old one again, but i'm going to keep trying to put it on the server. It's faster, has alot more ram, is really quiet.

So if I install ubuntu as a Server, so there's no XServer setup, can I later install Gnome without a CDROM or FLoppy, from the other machine? like, sudo dpkg-install xserver-xorg or something, something where it won't need the CDROM? Or is there a command in Linux so it'll read the CDROM, 'cause I -can- plug it in, I just can't boot from it.

Please, please help. It's greatly appreciated

---

### Post by dcstar on 2006-01-30
[QUOTE=Taigrr].......
So if I install ubuntu as a Server, so there's no XServer setup, can I later install Gnome without a CDROM or FLoppy, from the other machine? like, sudo dpkg-install xserver-xorg or something, something where it won't need the CDROM? Or is there a command in Linux so it'll read the CDROM, 'cause I -can- plug it in, I just can't boot from it.
.......[/QUOTE]
I believe installing the ubuntu-desktop package will install the X stuff onto a server install, and you should be able to set up a CD-ROM post-install to do it.

BTW, it's usually a very bad idea to move an installed system disk to different hardware, there are a lot of things set up and configured during the install phase which won't be done again if you change hardware (there is a very good reason it takes that long for an install, it just ain't copying files............)

---

