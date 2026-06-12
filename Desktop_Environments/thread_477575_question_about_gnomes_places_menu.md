---
title: "question about gnomes places menu"
date: 2007-06-18
forum: Desktop Environments
---

### Post by matt.raffel on 2007-06-18
I have been able to add a new "places" to the gnome places menu, like another PC in my home network. But these "places" are not in my /mnt folder so I can't access them from a terminal/console. Is there a way to make available to the terminal or do I just have to mount them manually?

thnx
Matt

---

### Post by Happy_Man on 2007-06-18
You gotta mount them manually, the places menu isn't really a frontend for the terminal, just a nifty bookmark feature.

---

### Post by dfreer on 2007-06-18
Depends on what protocol you use to access the other PC's in your network (I assume SMB?). Either way, pretty much any remote filesystem can be mounted to a folder, try checking out the Ubuntu Guide for How-to's for SMB, SSH, and FTP.

---

### Post by matt.raffel on 2007-06-19
> **Happy_Man said:**
> You gotta mount them manually, the places menu isn't really a frontend for the terminal, just a nifty bookmark feature.

Just curious, how does it work for the places browser when Im "browsing" a network device?  does it create a temporary mount somewhere?

---

### Post by mannheim on 2007-06-19
> **matt.raffel said:**
> Just curious, how does it work for the places browser when Im "browsing" a network device?  does it create a temporary mount somewhere?

There is no mount. The file browser (Nautilus) is using gnome-vfs (gnome virtual file system), which knows about the network protocols needed to access the networked machine. Unfortunately, not many applications -- even gnome applications -- support gnome-vfs, so you can't use these folders for much else.

There are alternative ways of accessing network resources -- ways which **do** create an ordinary mount. With these ways, the network resource becomes available to all applications.

---

