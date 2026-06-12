---
title: "Broken packages?"
date: 2006-09-30
forum: Desktop Environments
---

### Post by OpticalIllusion on 2006-09-30
When I open Synaptic Package Manager, it tells me that I have 5 broken packages.  When I filter them to see what all is broken, it wants to practically remove EVERYTHING that I've ever installed!  There's a huge list of stuff it wants to remove.  What the hell happened?

---

### Post by wieman01 on 2006-09-30
No idea what has happened. Hard to tell, but run this command from a terminal window & see if it helps:
> sudo aptitude -f remove

---

### Post by OpticalIllusion on 2006-10-01
The only thing I did was try to dpkg -i a debian of gnomebaker, which didn't work because of all the dependancies that I was missing.  After that, I got this broken package message.

If I do that command, it won't uninstall all of my programs will it?

It's even wanting to uninstall XGL + Beryl.

EDIT:  I went ahead and did that command.  It's fixed now.  Thanks.

---

### Post by ardchoille on 2006-10-01
> **OpticalIllusion said:**
> The only thing I did was try to dpkg -i a debian of gnomebaker, ..

This is one of the reasons why it's a bad good idea to use a package that is made for debian on an Ubuntu system.

---

