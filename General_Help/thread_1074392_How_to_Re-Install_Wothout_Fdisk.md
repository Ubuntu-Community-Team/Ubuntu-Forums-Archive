---
title: "How to Re-Install Wothout Fdisk?"
date: 2009-02-19
forum: General Help
---

### Post by matey3 on 2009-02-19
Oops sorry about the typo..(I meant to write "Without")! any way

I want to format the HDD in Feisty but I do not want to make any changes to the partitions.It is a 64 bit server...
How can I do a clean re-install using the CDROM?
Thanks!


in DOS we used to could format c: /q/s to do a quick format and put the system so it will boot.
is there such command in Linux/Ubuntu?


Thanks A Lot!


BTW what if I am ssh-ing to this server, and I cannot let the CDROM boot for me! bcs I wont be able to see the screen?

in either case your reply will be appreciated.

---

### Post by mcduck on 2009-02-19
use manual partitioning during the install, it will allow you to format the partitions you want.

---

### Post by matey3 on 2009-02-19
> **mcduck said:**
> use manual partitioning during the install, it will allow you to format the partitions you want.

OK Thanks for the reply. I saw that but I back out...

---

### Post by matey3 on 2009-02-19
Hello again;

Does anyone know how I could see the partition tables and the mount points?

When I do an fdisk -l ,I can see the partition table but I do not see the mount points and sizes (nly blocks??) and when I do the df -h I can see the size used but not other disk configuration information?
du also scrolls a lot of things on screen, which do not help (Or I dont know how to use it?)!

OK I have 2 servers A and B and I want to make this backup machine (B) exactly like the other main server(A). (each have the same disks 2 X 250 GB mirrored)..

How can I find out the mount points and sizes of my "A" (server) Partition without damaging it lol
These were set up by some one else whom I have never met!? So that is why I am here asking you.

Thank You for your help!

---

### Post by mcduck on 2009-02-19
just read them from /etc/fstab (which is the file where drive mounting is configured)

Or you can run "df -h" which lists mounted file systems, their mount points and used/available space.

---

### Post by matey3 on 2009-02-19
> **mcduck said:**
> just read them from /etc/fstab (which is the file where drive mounting is configured)

Or you can run "df -h" which lists mounted file systems, their mount points and used/available space.

Gee thanks a lot. That is like a very good idea. I'll check it out.
BTW where is the thank you button I dont see it any more? may be a different forum? heh... well any way, I appreciate the info.
Regards;

---

### Post by mcduck on 2009-02-19
The thank button and option for marking threads as solved were removed. I understood that they were causing some problems with the forum database.

---

