---
title: "Home dir properties don't match up to system monitor. Why?"
date: 2009-05-16
forum: General Help
---

### Post by Roasted on 2009-05-16
When I right click my home directory and hit properties, it says 170.3gb used.

When I open system monitor, it says 179.0 used.

The ONLY chance I made recently is I installed VirtualBox with two dynamically sized hard disks for two VM's I installed. Both hard disk VM's total 8.0gb inside of my ./VirtualBox folder.

Why am I seeing different numbers in system monitor versus home directory properties?

Note - My home directory is on its own partition.

---

### Post by dcstar on 2009-05-16
> **Roasted said:**
> When I right click my home directory and hit properties, it says 170.3gb used.

When I open system monitor, it says 179.0 used.

The ONLY chance I made recently is I installed VirtualBox with two dynamically sized hard disks for two VM's I installed. Both hard disk VM's total 8.0gb inside of my ./VirtualBox folder.

Why am I seeing different numbers in system monitor versus home directory properties?

Note - My home directory is on its own partition.

GiB <> GB

---

### Post by Roasted on 2009-05-16
> **dcstar said:**
> GiB <> GB

Hey, yeah.

What?

---

### Post by dcstar on 2009-05-16
> **Roasted said:**
> Hey, yeah.

What?

Look up the definitions.

---

### Post by MontelEdwards on 2009-05-16
Because one is more accurate than the other

---

### Post by Roasted on 2009-05-16
> **m.deonte said:**
> Because one is more accurate than the other

They've always matched since day 1. I don't see why it would make a difference now.

Not only that, but let's throw another curve ball into the mix. I have a script to rsync everything from my home directory to a spare 500gb drive in my computer. My home directory and this 500gb hard drive are 100% identical in terms of what files are on them. However, system monitor sees my home directory as 179.1 GiB and my 500gb spare drive is 179.9 GiB.

I know it's not much. But, seriously... why?

---

### Post by Roasted on 2009-05-16
> **Roasted said:**
> They've always matched since day 1. I don't see why it would make a difference now.

Not only that, but let's throw another curve ball into the mix. I have a script to rsync everything from my home directory to a spare 500gb drive in my computer. My home directory and this 500gb hard drive are 100% identical in terms of what files are on them. However, system monitor sees my home directory as 179.1 GiB and my 500gb spare drive is 179.9 GiB.

I know it's not much. But, seriously... why?

Well, I was able to answer one question. I forgot I had a torrent running. I was downloading 1 big torrent of several linux distros in one. So now in system monitor both my home directory and the 500gb drive that syncs to my home directory totals out to be 180.0 GiB.

My home directory is still seen as 170.3 GB when I check the properties of it, which is confusing considering that I HAVE been downloading all night and it never increased accordingly. So that part is kind of weird... but at least both my home directory and my backup drive match. That was strange seeing them be different.

Wonder why my home dir is read as 170.3 still? Even after the torrent finished...

---

### Post by 3rdalbum on 2009-05-16
When you start downloading a torrent, the file that gets created on your hard disk is the size that the final file will be.

If you mount a virtual filesystem inside your home directory, some programs will report your home directory's size with the virtual filesystem, some will report it without. In Gnome, Samba shares are mounted inside ~/.gvfs.

---

### Post by Roasted on 2009-05-19
I see. This all makes sense.

But one last question - When I'm looking at my disk usage and trying to think in my mind "okay I have x-amount of space left", which one is more accurate to take a look at?

GB?
GiB?

Is there a way to configure system monitor to read the disk data as GB or is it only GiB?

---

