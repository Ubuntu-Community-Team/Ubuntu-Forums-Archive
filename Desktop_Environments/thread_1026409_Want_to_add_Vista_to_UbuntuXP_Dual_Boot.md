---
title: "Want to add Vista to Ubuntu/XP Dual Boot"
date: 2008-12-31
forum: Desktop Environments
---

### Post by asphaltninja on 2008-12-31
I've been reading up on triple booting, and have two questions.

1. Can I add Vista to my existing Ubuntu/XP dual boot, and how?
2. Is this safe to do?
3. If it's not safe to do is there anyway that I could possibly overwrite the XP partition and use it for Vista and dual boot that with Ubtunu or would I have to start all over?

---

### Post by hawker525 on 2008-12-31
1. If you have enough free space on your hard drive,you can just partition it and install vista on that partition. Also, you'll need to edit your /boot/grub/menu.lst so vista will be displayed on startup.
2. As long as you don't touch your other partitions, you'll be fine.
3. You can always format your xp partition and install vista over it
Grub entry (assuming vista is on your third partition)
```
title Windows Vista
rootnoverify (hd0,2)
chainloader +1
```

---

### Post by asphaltninja on 2008-12-31
From what I've been told, I should install Vista from within XP to avoid any issues, correct? So I need to create another partition for Vista, install it and edit the menu.lst file to add Vista?

---

### Post by Martin Marshalek on 2008-12-31
Actually, from what I have read (and my own dual-boot experience), if you install Vista now, it will install it's own bootloader) and won't allow you to boot into Ubuntu from GRUB. Therefore, after installing Vista, you will need to find a way to reinstall GRUB. If you did everything correctly, it should automatically recognize Vista and XP.

---

### Post by euclidsbrother on 2008-12-31
> **asphaltninja said:**
> I've been reading up on triple booting, and have two questions.

1. Can I add Vista to my existing Ubuntu/XP dual boot, and how?
2. Is this safe to do?
3. If it's not safe to do is there anyway that I could possibly overwrite the XP partition and use it for Vista and dual boot that with Ubtunu or would I have to start all over?

Why not run Vista and XP as virtual machines on top of Ubuntu?  Then you can boot either (or both) while still using Ubuntu.  Check out VirtualBox.org.  I love the seamless mode.. It makes it look like i'm running windows apps in Ubuntu... :)

-EB

---

### Post by hawker525 on 2009-01-01
What M.M. says is right (forget to mention it), but I've heard the Super Grub Disk is a very handy tool to restore and/or install GRUB. I've had no experience with this, so it's just speculations.

---

### Post by asphaltninja on 2009-01-01
Ok so I decided to just backup my stuffs and start over. I installed XP and created three partitions, then formatted them through XP.

1 for XP
1 for Vista
1 for Ubuntu/file storage

I boot into Ubuntu and now I'm at the "Prepare Paritions" window. I resized the third partition, creating a 10gb space for Ubuntu and a 1gb one for swap. I selected "etx 3" and "swap" respectively for the "use as" option. I want to use the remainder for file space.

My question has to do with mount points. As of right now, the only one with a mount point listed in the "Prepare partitions" window is the one that I'm going to install Ubuntu on. I have "/" selected. Should there be mount points selected for the other partitions? I didn't use the Ubuntu partitioner to create them, I did it in XP during setup if that helps at all. The only editing I did in Ubuntu was to resize the third partition. As I said I want to use the leftover space from this for file storage.

Sorry for the lengthy post, any help would be greatly appreciated.

---

### Post by tad1073 on 2009-01-01
> **asphaltninja said:**
> Ok so I decided to just backup my stuffs and start over. I installed XP and created three partitions, then formatted them through XP.

1 for XP
1 for Vista
1 for Ubuntu/file storage

I boot into Ubuntu and now I'm at the "Prepare Paritions" window. I resized the third partition, creating a 10gb space for Ubuntu and a 1gb one for swap. I selected "etx 3" and "swap" respectively for the "use as" option. I want to use the remainder for file space.

My question has to do with mount points. As of right now, the only one with a mount point listed in the "Prepare partitions" window is the one that I'm going to install Ubuntu on. I have "/" selected. Should there be mount points selected for the other partitions? I didn't use the Ubuntu partitioner to create them, I did it in XP during setup if that helps at all. The only editing I did in Ubuntu was to resize the third partition. As I said I want to use the leftover space from this for file storage.

Sorry for the lengthy post, any help would be greatly appreciated.

That will be fine the way you have it.

---

### Post by asphaltninja on 2009-01-01
> **tad1073 said:**
> That will be fine the way you have it.

Ok, but when I click forward it warns me that if I don't specify a mount point for sda6 (the one I want to use for file space) that it won't be used for anything. 

Does this just mean that the OS itself won't be installing anything on it, but I'll still be able to use it to store files on?

---

### Post by hawker525 on 2009-01-02
Your sda6(Ubuntu) partition should have the ext3 FS and mountpoint /.
btw: If you want to be able to access you windows partitions, you should assign mountpoints to them. Either in install or afterwards by gparted.

---

### Post by award982 on 2009-01-02
> **hawker525 said:**
> Your sda6(Ubuntu) partition should have the ext3 FS and mountpoint /.
btw: If you want to be able to access you windows partitions, you should assign mountpoints to them. Either in install or afterwards by gparted.
 
what tha hell is mountpoints?:confused::confused::confused:

---

