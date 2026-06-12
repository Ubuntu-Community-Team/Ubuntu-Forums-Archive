---
title: "VFS: can't find ext3 filesystem on dev hda1"
date: 2005-03-30
forum: Desktop Environments
---

### Post by KDE-fan on 2005-03-30
I just upgraded to the newest version of some of the kubuntu packages (150 megs), and I now get a funny message every time the computer boots:  
  
"VFS: can't find ext3 filesystem on dev hda1" 
  
Other than that, the system starts perfectly.  
Q: What is the true meaning of this message?  
Q: How do I fix it?  
On my computer, hda1 is reiserfs, and that shouldn't be any problem. 
 
The fstab entry for hda1 is  
/dev/hda1       /               reiserfs notail         0       0

---

### Post by techlord on 2005-03-30
i think this is just an informational message and can just be ignored

---

### Post by Juergen on 2005-03-30
Before Ubuntu I always built my own kernels and never used an initrd, so I'm not sure ;-)
but I think it's just the kernel saying 'I can only read ext3, so now I'll need some drivers from initrd to boot from this partition'

AFAIK I've had this since first installing Ubuntu. Are you sure this message is new?

---

### Post by KDE-fan on 2005-03-30
OK, I guess it is not something serious then. I am not 100% sure that this message is a new one either, since I normally don't read all the stuff that show up when the computer boots.   
  
One thing have changed though, the checking of one of my reiserfs-partitions used to give a red [failed] when the computer booted. I now get a [ok] or something instead. I reformatted that particular partition from NTFS to reiserFS after I had installed Kubuntu, and it have never failed to mount perfectly.

---

### Post by neighborlee on 2005-03-30
[QUOTE=KDE-fan]I just upgraded to the newest version of some of the kubuntu packages (150 megs), and I now get a funny message every time the computer boots:  
  
"VFS: can't find ext3 filesystem on dev hda1" 
  
Other than that, the system starts perfectly.  
Q: What is the true meaning of this message?  
Q: How do I fix it?  
On my computer, hda1 is reiserfs, and that shouldn't be any problem. 
 
The fstab entry for hda1 is  
/dev/hda1       /               reiserfs notail         0       0[/QUOTE]
----------------
I get this as well on everyboot..it hangs there for a bit ( i'm using reiserfs in hoary atm ) and would like explanation as to why this message is displaying and if there is a fix in the works ?

cheers
nl

---

### Post by rum beverage on 2005-04-17
i am getting this same issue with hoary after moving my install from a ext3 partition to a reiserfs partition.

edit: take that back, it's not really an issue as everything seems to boot fine.  but it would be nice to know why it is doing this.

---

### Post by mgor on 2005-04-17
it's 'probing' for what filesystem the root have (or atleast that's my guess), check dmesg and you'll see it tries ext2 first.

check out /etc/mkinitrd/mkinitrd.conf
> ... that are needed to mount the root file system...

---

