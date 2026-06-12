---
title: "How To Reinstall Windows and not lose Grub"
date: 2006-01-03
forum: Desktop Environments
---

### Post by Draconis on 2006-01-03
Is it possible to reinstall Windows and not lose Grub on a dual boot system?
If not is there a way to reinstall Grub without losing my current Linux setup?
My Windows installation is showing signs of needing a reinstall to fix some problems, I still need it as there are some programs I use that I have yet to find a Linux equivalent.

---

### Post by darkpark on 2006-01-03
no, there isn't.   the windows install will overwrite the MBR (master boot record) but this issue is easy to resolve.
after you install windows, boot from your ubuntu CD and select the recovery option.
once you're at the command prompt, simple re-run the grub config/setup.  i don't know the specifics of reconfiguring grub, but if you search these forums than you should be able to find the answer or someone hopefully replies to this thread with a more complete answer.

---

### Post by joneZ on 2006-01-03
You can do do this, but you have to make sure not to delete an partition

1. 

Download knoppix ( the live linux )

2. 

Install the windows is the same partition as it where before . DO NOT EDIT OR REMOVE
the partitions in the Windows setup menu. But you can format the windows partition.

The stand something like

c: NTFS 
d: unsportted type 
e: vfat 


Just select ... install into C:

3. 
Now your windows has overwritten the mbr. But the ubunut partition is still there.


4. 

Now
- Boot knoppix 

- get a root console

- goto /mnt and type mkdir ubuntu or something else 

- mount your Ubuntu partition into /mnt/ubuntu

- and now do a chroot with the command 'chroot /mnt/ubuntu'

- type 'grub-install'  and 'update-grub'

- shutdown and there is your grub again with link to start MS already included



I have done this so .. but maybe it should work with the recovery cd instead of knoppix to. The most
imported thing is that you NOT delete any partitions or Move/Resize whatever.

Bye
Erik

---

### Post by bluemuffin on 2006-01-03
I am facing the same problem, have to reinstall XP on a dual boot system. 

I have 2 hard drives, 1 for XP and 1 for Ubuntu-breezy. Will the process still be the same? Is there no way that the Ubuntu CD be used to re-install the grub loader?

Tnx.

---

### Post by apparition on 2006-01-04
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Assuming your Ubuntu Install CD worked to set up Grub initially, the above site will help you out.  You might be able to skip partitioning (ie. steps 2-7) if you press 'Esc' at your first opportunity when prompted with something.

---

### Post by Draconis on 2006-01-05
Thank you all for the assistance. Will rebuild Windows soon and try the suggestions. Will post results.

---

### Post by brohan on 2006-01-06
I've ran into the exact same problem, and used the method using Knoppix and it worked like a charm.
Just to let you know that it worked for me ;)

---

### Post by xenomorf on 2006-01-06
[QUOTE=apparition][http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Assuming your Ubuntu Install CD worked to set up Grub initially, the above site will help you out.  You might be able to skip partitioning (ie. steps 2-7) if you press 'Esc' at your first opportunity when prompted with something.[/QUOTE]
Will the above mentioned method create a grub that is able to boot Windows as well or just ubuntu?

---

