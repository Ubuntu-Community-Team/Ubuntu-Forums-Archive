---
title: "linking a file?"
date: 2009-01-22
forum: General Help
---

### Post by quinnten83 on 2009-01-22
I use dropbox to keep some data synchronised.
I was wondering if there might be a way to place my liferea folder in the dropbox folder, and have perhaps a link in my homefolder that refers to that folder. That way I can keep all the liferea synchronised.
Does anybody have any experience with this, or is this at all possible?

Let me know

---

### Post by oaqster on 2009-01-22
**ln** is your friend...

```
man ln
```

in a terminal for more details, alternatively you can also simply right click on a file or folder and select "Make Link", which will create a link to it in the same folder, now move that to where ever you want to link from & your done - you might want to rename the link :)

---

### Post by cmnorton on 2009-01-22
cd <folder-containing-link>

ln -s <full-path-to-folder> <link-to-folder-name>

so if you are in /home/you

ln -s /dropbox dropbox

---

### Post by quinnten83 on 2009-01-22
okay, 
so if i move my .liferea folder that was in my homefolder and contained all the configuration data for liferea to my /dropbox folder and place a link in my homefolder called .lifera, that refers to my .liferea folder now in my dropbox, Liferea should still open normally right?
Which means that if i have another ubuntubox, i can do the same and all the liferea on all the linuxboxes would share the same data right?

---

### Post by Yashiro on 2009-01-22
Holding middle mouse, the wheel, while dragging and dropping in nautilus lets you create links.

---

### Post by cmnorton on 2009-01-22
> **quinnten83 said:**
> okay, 
so if i move my .liferea folder that was in my homefolder and contained all the configuration data for liferea to my /dropbox folder and place a link in my homefolder called .lifera, that refers to my .liferea folder now in my dropbox, Liferea should still open normally right?
Which means that if i have another ubuntubox, i can do the same and all the liferea on all the linuxboxes would share the same data right?

As to question 1, it should open fine, but you'll know more if you experiment with something that's not critical..

If several ubuntubox-es all expect to use the same folder, that too should work.

While you are being encouraged to use the gnome menu and that is not a bad thing, I believe implementing the link this way gives you a better understanding of what a link is (IMHO).

---

### Post by quinnten83 on 2009-01-24
I understand the linking idea. But in linux it kinda works in a different manner, as you can make symbolic links and hard links.
The difference between the two escapes me at this moment.

By the way, it sorta works.
I have all the same links everywhere, but it does not synchronise what I have already read to all computers.
I guess half a success is better than none at all?

---

### Post by dcstar on 2009-01-24
> **quinnten83 said:**
> I understand the linking idea. But in linux it kinda works in a different manner, as you can make symbolic links and hard links.
The difference between the two escapes me at this moment.
........

A symbolic link works across mounted filesystems, a hard link only applies to the same filesystem (it is like another directory entry pointing to the same file area on the disk).

Be aware that linking to non-Linux filesystems may cause problems if the filesystem does not support the full privileges/security that native Linux filesystems provide - especially if you are moving directories that the application assumes will be on a Linux filesystem.

---

