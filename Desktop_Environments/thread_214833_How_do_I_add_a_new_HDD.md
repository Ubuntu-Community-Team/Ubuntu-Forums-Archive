---
title: "How do I add a new HDD?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Sunnz on 2006-07-13
Say I brought a new Hard Disk, just an ordinary, IDE, 3.5inch one for desktop... how do I install it? It surely wouldn't just work if I just plug in the IDE and power cables and just added to the OS, like Windows, would it? Do I have to edit /etc/fstab before I install the hard drive?

---

### Post by philippe_carlo on 2006-07-13
You can just plug it, partition it and install winows likr that. BUT ...

(1) After installing windows, you will have to install grub again to your Master Boot Record
(2) You will have to add windows to the grub menu in /boot/grub/menu.lst
(3) And yes, if you want to be able to comfortly access the windows partitions, you may want to add them to /etc/fstab

---

### Post by Sunnz on 2006-07-13
What are you talking about?

---

### Post by Sunnz on 2006-07-13
My computer already have Linux installed. Now I have brought a new hard disk because I want more space. I am not asking how to install an OS but how to install a new HD such that Linux can detect it... Windows normally detects new HD automatically.

---

### Post by moimies on 2006-07-13
1. Plug in the cables
2. Configure your bios so that bios detects it.
3. Boot to Ubuntu
4. Make partition with partitioning tool...I'm not sure about it's name
5. Mount partition, if it doesn't mount automagically...not sure about this one either :)

---

### Post by Sunnz on 2006-07-13
4, fdisk?

So I can just plug it in and Linux would still boot? Great! Thanks!

---

### Post by moimies on 2006-07-13
Of course it will, if you don't remove the old one that has Ubuntu in it.

---

### Post by AZzKikR on 2006-07-13
> **Sunnz said:**
> 4, fdisk?

So I can just plug it in and Linux would still boot? Great! Thanks!
Use GParted to manage partitions.

sudo apt-get install gparted

to install it!

---

### Post by philippe_carlo on 2006-07-13
I misunderstood and thought you wanted to install Wondows on the second HD.

If not, it becomes much easier. You just have to partition the hard disk (using fdisk, for instance) and add those partitions to /etc/fstab for convenience.

---

### Post by DigitalXpert on 2006-07-13
The tool is called **qtparted**.You can also use **gparted**.  They are both GUI frontends to the command line tool **parted**.

After you partition the disk you will have to add an entry in **/etc/fstab**.  Read the man page about it if you need help with the syntax, etc.  Type at a terminal:

[INDENT]*man /etc/fstab*

or maybe just

*man fstab*
[/INDENT]
Hope this gets that drive up and running for you.  Then you can get busy filling it with legally downloaded mp3s and movies. [I];)
[/I]

---

