---
title: "1tb external drive"
date: 2009-06-24
forum: General Help
---

### Post by blur xc on 2009-06-24
I'm trying to migrate all my junk over to a new Ubuntu machine, and one of the open items on my list is moving my external 1tb drive over (ntfs file system).  Right now it's plugged into a USB port on our old PC, but I want ot plug it in to an eSATA port on the new computer.  And it's got about 300gigs of junk on it...
 
So, I guess my question isn't so much Ubuntu related, rather than eSATA, but are eSATA ports hot swappable?  Or do I need to shut it down every time it will be disconnected (won't be often).  Also, do I need to remember to plug it into the same eSATA port every time?
 
The 2nd item after that, which I may figure out on my own just fine, is makign the drive visible to Vista runnign in VBox...
 
BM

---

### Post by capscrew on 2009-06-24
> **Barna Madau said:**
> I'm trying to migrate all my junk over to a new Ubuntu machine, and one of the open items on my list is moving my external 1tb drive over (ntfs file system).  Right now it's plugged into a USB port on our old PC, but I want ot plug it in to an eSATA port on the new computer. 
Does the drive have a SATA header?> 

 And it's got about 300gigs of junk on it...
 
So, I guess my question isn't so much Ubuntu related, rather than eSATA, but are eSATA ports hot swappable? 
The question is more "are the partitions hot mountable?" Can I automount it?  There should be no problem plugging in the drive it will be powered up and recognized.> 

 Or do I need to shut it down every time it will be disconnected (won't be often).  Also, do I need to remember to plug it into the same eSATA port every time?
I run a eSATA connected drive. I mount it via a script.  I don't think it matters which header port you use.  The partitions should be ID'd via UUID.  I umount the partition before I unplug the drive.> 
The 2nd item after that, which I may figure out on my own just fine, is makign the drive visible to Vista runnign in VBox...

Hmmmmmm> 


 
BM

---

