---
title: "&quot;places&quot; won't find all my partitions"
date: 2009-04-04
forum: General Help
---

### Post by AndersBrontosaurus on 2009-04-04
Hi! I am quite new to the Linuxscene. Have used Kubuntu for a while but is now exploring Xubuntu which seems neater to me. I just have one question: The little button named "places" does not find the ntfs-partitions on my internal HDD:s. It does however find the external NTFS-HDD. Can anything be done about this?It would help a lot. 
Thanks for helping.

Anders

---

### Post by mb_webguy on 2009-04-04
Only removable media (i.e. drives and partitions mounted in the /media directory, like USB drives) will show up in the Places menu.  Partitions on internal drives are accessed by navigating to the directory where they are mounted.  For example, if you mounted a partition as /home, then when you go to /home or any directory under /home, then you're using that partition.

Linux uses what's called a unified file system.  Unlike Windows, partitions are just another directory in the filesystem, rather than a distinct "drive".

---

### Post by AndersBrontosaurus on 2009-04-05
Yes, but all my partitions, both internal and external are mounted in /media.... so I still don't get it.

---

### Post by -kg- on 2009-04-05
Have you looked under "Removable Media?"  That's where I found mine.

I didn't even know they were listed there.  I always go ahead and launch Nautilus with the "Computer" button and they are listed there, as well.

---

### Post by coffeecat on 2009-04-05
> **-kg- said:**
> I always go ahead and launch Nautilus with the "Computer" button and they are listed there, as well.

But that's with Gnome. The OP is using Xubuntu, which uses the Xfce desktop. The few times I've tried Xubuntu, automounting was not as good as in Ubuntu. In fact the whole way Xfce dealt with partitions/drives seemed far less elegant than in Gnome.

> **AndersBrontosaurus said:**
> Yes, but all my partitions, both internal and external are mounted in /media.... so I still don't get it.

Sorry, I'm not really familiar with the Xfce desktop, but... Can you navigate to the internal ntfs partitions via /media in the file manager? If not, post the contents of /etc/fstab, and the terminal output of:

```
sudo fdisk -l
```and someone should be able to help.

---

### Post by ShaunG on 2009-04-05
I run xubuntu and I use nautilus whenever I want to access my other internal drives with a GUI.

Install nautilus, then press alt+f2 and type 

nautilus --no-desktop


It's not perfect, but it works.

---

### Post by -kg- on 2009-04-05
> But that's with Gnome. The OP is using Xubuntu, which uses the Xfce desktop.

LOL!  I'm going to have to pay closer attention.

Also, I thing that I'm going to have to install all the desktop managers (KDE, Xfce, etc.) if I'm going to be much help to anyone who doesn't use Gnome.

:popcorn:

---

### Post by AndersBrontosaurus on 2009-04-08
Thanks for helping!

Still I haven't found a neat way. maybe I'm unclear with my problem. I have no problem in finding all my partitions if I'm doing it the traditional way with clicking around in thunar. What I'm looking for is a simple shortcut to access all of them (and no, I don't want to have them as icons on the desktop :-) ). therefore- "places". it seems so good but then again doesn't find all my partitions. 

Anders

---

