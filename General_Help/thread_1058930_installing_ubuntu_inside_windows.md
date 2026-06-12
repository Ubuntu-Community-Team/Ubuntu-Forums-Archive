---
title: "installing ubuntu inside windows"
date: 2009-02-03
forum: General Help
---

### Post by Hutom on 2009-02-03
If I install ubuntu inside windows then will ubuntu run independent of windows or it runs as a program inside windows? 

Is it EXACTLY SAME as installing ubuntu in a separate partition (which I have done previously while having dual boot)? If not what is the difference?

---

### Post by happysmileman on 2009-02-03
It will run independently, but AFAIK the "file system" will actually just be a file on the Windows partition, so if Windows gets a virus or something then you lose Ubuntu too. It's also supposed to be slower than running it as a separate partition (but still much faster than LiveCD).

EDIT: I assume you mean Wubi, and not a VM as next poster mentioned.

---

### Post by smothpocket on 2009-02-03
If you are reffering to a program like wubi then it runs almost exactly the same as a dual boot. It just stores a virtual hard disk file on your windows partition.

If you're thinking of creating a virtual machine then there will be some restrictions compared to a dual boot system. Mostly graphical restrictions.

---

### Post by Sealbhach on 2009-02-03
Incorrect, ignore.

.

---

### Post by Hutom on 2009-02-03
Thanks to all of u. Just two questions.

1) While booting is it like windows will boot first and then ubuntu will boot?

2) Does it require more ram compared to dual boot?

---

### Post by FuturePilot on 2009-02-03
> **Sealbhach said:**
> I think the biggest difference is as mentinoed above, Wubi will use the Windows Filesystem, not its own ext3.

I see people say it's a bit slower as well, not sure if it's only due to the Windows Filesystem or some other factors.

.
Linux can't run on NTFS. The virtual disk the Wubi creates is formated as Ext3 just like a real install.

> **Hutom said:**
> Thanks to all of u. Just two questions.

1) While booting is it like windows will boot first and then ubuntu will boot?

2) Does it require more ram compared to dual boot?

1) You can only be booted into 1 operating system at a time. When you turn your computer on the Grub boot loader will appear allowing you to choose which OS you want to boot.

2) No. Using Wubi *is* dual booting, just without having to repartition your hard drive.

---

### Post by bapoumba on 2009-02-03
Moved to Wubi.

---

### Post by Hutom on 2009-02-04
> **FuturePilot said:**
> Linux can't run on NTFS. The virtual disk the Wubi creates is formated as Ext3 just like a real install.



1) You can only be booted into 1 operating system at a time. When you turn your computer on the Grub boot loader will appear allowing you to choose which OS you want to boot.

2) No. Using Wubi *is* dual booting, just without having to repartition your hard drive.

Thanks for all the responses. But I'm still a bit confused. See I don't really know much of the technicalities. I'm just an ordinary user. But if FuturePilot is right then what is this website saying? There seems to be a contradiction. 
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

See the 1st and 3rd disadvantages.

---

### Post by Darkmage09 on 2009-02-04
Ive used Ubuntu on Microsoft Virtual PC 2007, The only problem I had was No sound, and unable to connect to the internet. But Windows XP and Windows 7 both have sound and could connect to the internet.

Ive never tried VirtualBox and I herd that MS VPC '07 is much faster anyways. It is fast, but it slows down Vista.

---

### Post by Ed. Yang on 2009-02-05
Just to share my Wubi/Ubuntu installation experience with HUTOM.

When you run execute Wubi installation, the programs will eventually tries to detect your on-board processor and the proceeds with the most suitable distro for download.

Like mine, Turion64 x2, the programs goes forward to download 64bit O.S for installation.
Using Wubi to download the operating system can be very slow... even with wifi broadband or wired, the transfer rate can be as low as 15kbps.

To speed up the process faster, you may want to download the O.S of your choice and later paste into one of the folder, which was created after you have run Wubi for the first time.
It works even you've chosen to go for 32bit Ubuntu.

After the operating system installed, if you're using xp initially, you may find that there's a big "red patch" shown if you run windows disk defragmentation with the program keep prompting you to do defragging.
Don't be alarmed though, as this "red patch" is actually the "Ubuntu Mice" that's siiting on the XP Bull...aka the hidden portion which windows is unable to determine if it is "system friendly" or not.

---

### Post by Ed. Yang on 2009-02-05
After installation, one of the difficulties i've faced, is to get the on-board wireless work.

I don't have wireless broadband at home, not even wired ones. But that's not really a big problem, because there's an existence of such "friendly" driver hidden in Ubuntu which you can use to run with external USB wireless adaptors to download the correct drivers for your system's on-board wireless card.

One thing to highlight though, my installation of Ubuntu was sitting on the XP drive without further partition. Hence i was unable to access NTFS files that was originally present in XP.

---

### Post by mikebailey on 2009-02-26
the wubi install is a great option really. solves the problem of ubuntu making windows running off with its ntldr and boot.ini between its legs and killing windows on the dual boot. but i had a question. i had a breif glimpse of genious i think, and i was curios what the community thought. now, i have a partition setup specifically for the wubi install of linux. now, what if that partition was formatted to ext3 and i also had ext2ifs installed so i could read and write to that partition and installed wubi in there. do you think it would speed up ubuntu, as on the ntfs drive with the virtual disk, it is a bit sluggish. thank you for your time

---

