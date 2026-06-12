---
title: "How do I resize/EXPAND my boot partition?"
date: 2020-10-03
forum: Desktop Environments
---

### Post by Mugsy323 on 2020-10-03
I need to make my boot partition larger, but nothing seems to permit it.

I tried GParted from a LiveUSB, as well as various Partitioning apps from Windows, and nothing will allow me to increase the size of my Ubuntu ext4 boot partition, only shrink it (I have 16GB of unallocated free space above it.)

When I first installed Ubuntu (Dual-boot PC), I only created a small 32gb partition for it. Now I'm running out of space and need to make my boot partition bigger.

I can clone/move the entire partition, but then the destination is the same size and I'm right back where I started.

There MUST be a way. TIA.

---

### Post by CelticWarrior on 2020-10-03
Partitions can be expanded ONLY if there's unallocated space AFTER it.
If the space is before then you need to move the partition first then expand it.

---

### Post by Mugsy323 on 2020-10-05
By "Above" I meant "After".

---

### Post by ActionParsnip on 2020-10-05
If you remove unused kernels it will free space and you won't need to resize (Unless you only have 1 kernel installed)

---

### Post by hk42 on 2020-10-05
I wonder what can be the use of a 32GB boot partition ?
I'm using less than 32GB root partition and /boot is part of it.
Only /home is on an external SD card and it is very handy.
Data and a few appimage are shared via samba from a NAS.

---

### Post by ajgreeny on 2020-10-05
I think we have  a problem of nomenclature relating to partitions here; is this really a 32G /boot partition or do you mean a / (root) partition on which the whole operating system usually sits?

To make matters more clear and easy to be sure what you really have on disk a screenshot of the gparted window would help.
Also please show the output of terminal commands ```
sudo fdisk -l
df -hT
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by TheFu on 2020-10-05
32GB for boot?!! That's huge!  Here's mine
```
$ df -Th
Filesystem                            Type  Size  Used Avail Use% Mounted on
/dev/sda2                             ext2  721M  148M  537M  22% /boot
/dev/sda1                             vfat  511M  3.7M  508M   1% /boot/efi
```

That's 720MB for boot and 512MB for efi stuff.  As you can see, both would fit into 500MB, but I like having a little extra room.

---

### Post by jbh54enwiler on 2020-10-09
I'm having the same issue making my root partition bigger in KDE Partition Manager on Kubuntu.  I was worried I'd have to delete the partition and reinstall the OS to get it to use the blank space I allocated, but CelticWarrior said I just need to move the blank space to above it?  How do I do that?[URL="https://ubuntuforums.org/member.php?u=1826209"]
[/URL]

---

### Post by TheFu on 2020-10-09
Boot from any Ubuntu Desktop install flash drive, then you can use gparted to shift and resize.  If the UUID changes for any of the partitions, you'll need to manually edit the /etc/fstab file for the new UUIDs.  I don't know/recall what sorts of changes cause the UUID to change. Sorry.

For me, fixing the UUID in an fstab is about 30 seconds of effort, so if storage fails after I'd screwed with partitions, that's the first thing I check.  **blkid** will show the current device <--> UUID mapping. Use **sudoedit** to modify the correct fstab.

---

### Post by jbh54enwiler on 2020-10-09
Where exactly where I find the UUID in case they do get changed?  And would fixing the issue be as simple as just changing the numbers in the file and saving it?  (Forgive me if this is something I should know, I've never had to modify system files before)  In addition, would Ubuntu GNOME come pre-installed with Gparted?  My system's wi-fi card doesn't play too well with Kubuntu out of the box, and I'm going to guess it's going to be the same problem with standard Ubuntu.  I'd still be able to download it over ethernet though, so it's not too much of a problem.

---

### Post by TheFu on 2020-10-09
Thought I'd answered that already.

> **blkid** will show the current device <--> UUID mapping. That is a command.

Look at the /etc/fstab file now.  
The fstab is 1 record per line.  
No wrapping of lines is allowed.  
1 line = 1 mount location.  
It is a text file. 
It is pretty simple, but don't mess up the spacing. Parts with 1 or more spaces need to have at least 1 space retained. Parts with no spaces need to have no spaces.  
**man fstab** explains what each field is.  If you google "ubuntu fstab" you'll find some results at help.ubuntu.com with lots more details.

---

### Post by jbh54enwiler on 2020-10-09
Ok, I got Gparted working on a live USB.  I couldn't figure out how to move the partitions, but I think I have an idea l.  Gparted gives me the option to copy/paste partitions, so would I be able to copy the existing root partition into the free space then delete the old root?

---

### Post by ActionParsnip on 2020-10-10
What is the output of
```

uname -a; dpkg -l | grep linux-image

```

Thanks

---

### Post by TheFu on 2020-10-10
> **jbh54enwiler said:**
> Ok, I got Gparted working on a live USB.  I couldn't figure out how to move the partitions, but I think I have an idea l.  Gparted gives me the option to copy/paste partitions, so would I be able to copy the existing root partition into the free space then delete the old root?

Moving takes a long time, especially shifting to the left. It is a drag-n-drop thing, assuming you've made space to-the-left already.

We've asked for command output a few times to ensure you don't actually do any really bad damage, yet I don't see it. If you actually want suggestions, please post the requested commands and output.

jbh54enwiler, you should open a new thread and not hijack this one. That is how this forum works best. Similar issues seldom are.

---

