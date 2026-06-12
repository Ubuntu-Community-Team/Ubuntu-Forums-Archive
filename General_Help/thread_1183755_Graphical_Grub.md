---
title: "Graphical Grub"
date: 2009-06-10
forum: General Help
---

### Post by Quarkrad on 2009-06-10
Have 9.04.  Been trying since 8.04 to get graphical grub working - still no luck - I would like the message.ubugrey background.   I think I'm almost there but I cannot get past a certain point. 

When I type _find /boot/grub/stage1_ in terminal I get a message that the file does not exist.  If I could get past this stage I need to type
root (hd0.0)  followed by setup (hd0)  and the new grub is set ready for boot.  When I look in boot/grub all the files are there (e.g. menu.lst, stage1, stage 2, etc).

So I put everything back (the old grub folder) and Ubuntu boots with the standard txt grub.  Again, all the files are in boot/grub.  But, strange to me, when I type sudo grub followed by find /boot/grub/stage1 I get the same missing files message. Yet it all works/loads.

Now I do not know if the error I had trying to get the graphical grub to work was due to me or not.  Surely on a standard working system I should not get an error message?

---

### Post by Legace on 2009-06-10
Did you enter
```
sudo grub
```

before find /boot/grub/stage1?

---

### Post by Quarkrad on 2009-06-10
Yes - this is what I get (on my standard working system):]



dad@hp:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.


   GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub> 



I dual boot Ubuntu and xp so I'm happy with root (hd0,0) and setup (hd0) to get my grub back (I've had t rebuild a couple of times).  My grub folder is in Filesystem/boot/grub and all the correct files are in there - weird above it says Error 15:  file not found

Thanks

---

### Post by Legace on 2009-06-11
Does the** /boot/grub/stage1** file exist?
Check it with Nautilus.

---

### Post by Quarkrad on 2009-06-12
Yes.  If I run terminal and have a look I get this:

dad@hp:~$ cd /boot/grub
dad@hp:/boot/grub$ ls
default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2
dad@hp:/boot/grub$ 



Something I do not understand:  If I type **sudo grub** and get the **grub>**  prompt am I sitting at /boot/grub?   If I type ls at grub> I get Error 27: Unrecognized command

---

### Post by colau on 2009-06-12
> **Quarkrad said:**
> Yes.  If I run terminal and have a look I get this:

dad@hp:~$ cd /boot/grub
dad@hp:/boot/grub$ ls
default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2
dad@hp:/boot/grub$ 



Something I do not understand:  If I type **sudo grub** and get the **grub>**  prompt am I sitting at /boot/grub?   If I type ls at grub> I get Error 27: Unrecognized command
Strange problem.
Can you post
```

cd /boot/grub/
ls -l

```
Did you run these command booting with ubuntu live cd?
```

sudo -s grub
find /boot/grub/stage1

```

---

### Post by Quarkrad on 2009-06-12
Thank you very much for your help.  The output to your commands is:

dad@hp:~$ cd /boot/grub/
dad@hp:/boot/grub$ ls -l
total 216
-rw-r--r-- 1 root root    197 2008-12-13 16:03 default
-rw-r--r-- 1 root root     30 2008-12-13 16:03 device.map
-rw-r--r-- 1 root root   8108 2008-12-13 16:03 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-13 16:03 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-13 16:03 installed-version
-rw-r--r-- 1 root root   8712 2008-12-13 16:03 jfs_stage1_5
-rw-r--r-- 1 root root   5095 2009-05-21 08:31 menu.lst
-rw-r--r-- 1 root root   4607 2009-05-21 08:31 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-13 16:03 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-13 16:03 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-13 16:03 stage1
-rw-r--r-- 1 root root 121460 2008-12-13 16:03 stage2
-rw-r--r-- 1 root root   9556 2008-12-13 16:03 xfs_stage1_5
dad@hp:/boot/grub$ 

I am not using the live CD to setup the new graphical grub - it is all done within the working app.   After I put all the new files in the grub folder and amend the menu.lst file it says type sudo grub and then find /boot/grub/stage1.  This is all the get the new grub setup. (After the find /boot/grub/stage1 there is the usual root (hd0,0),setup (hd0)).

---

