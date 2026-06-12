---
title: "Lost NTFS partition, any way to recover?"
date: 2009-01-29
forum: General Help
---

### Post by Icy9999 on 2009-01-29
Hello, I tried to install Ubuntu today for the first time and even though I had defragged my hard drive overnight I still got a message saying "No operating system found" or similar during boot.

I am now using the LiveCD and GParted shows my Windows NTFS partition (515gb) as Unknown with an exclamation mark next to it. There is no other option than format to a file system.

I know I am not going to get away with this easily, I had already backed up most of my data, but is there any way I can access the files through Ubuntu and burn some of them to DVDs before formatting it?

---

### Post by Piraja on 2009-01-29
First of all, don't panic: you have not necessarily lost any data yet. However, I think you should see in GParted also an option to resize the partition. In any case, do not format your NTFS partition, because I think you will still be able to recover it. This is a just a preliminary remark, until someone more knowledgeable comes along to help you... I mean, I've been there, but I'm not sure which is the best way to proceed now. Good luck!

---

### Post by Icy9999 on 2009-01-29
Resizing the partition is not possible now, the option is not there anymore.
The 80gb partition I created for Ubuntu is now "unallocated" too.

Edit: A little bit of google search came up with a program called "TestDisk" that can supposedly help me. However I'm a bit clueless when it comes to Linux since this is the first time I use it, I suppose the right thing to do would be to download the Linux version then what? It's a .tar.bz2 file.

---

### Post by Piraja on 2009-01-29
> **Icy9999 said:**
> Resizing the partition is not possible now, the option is not there anymore.
The 80gb partition I created for Ubuntu is now "unallocated" too.
I don't think you should need the mentioned application. "Unallocated" means free space, in which you can create a new file system, i.e. space that you can use to install Ubuntu. So it seems that you have not actually installed anything yet (or even formatted the 80 GB partition for Ubuntu). Now could you check if the NTFS partition is mounted? That would prevent resizing it. Actually you do not need to resize it at the moment, if you want to install Ubuntu to the unallocated (free) space on you hard disk. 

I will return in a minute to explain how to check if the partition is mounted and how to unmount it &#8212; in case you still want to use the partitioning tool (GParted) on it.

---

### Post by Icy9999 on 2009-01-29
> **Piraja said:**
> I don't think you should need the mentioned application. "Unallocated" means free space, in which you can create a new file system, i.e. space that you can use to install Ubuntu. So it seems that you have not actually installed anything yet (or even formatted the 80 GB partition for Ubuntu). Now could you check if the NTFS partition is mounted? That would prevent resizing it. Actually you do not need to resize it at the moment, if you want to install Ubuntu to the unallocated (free) space on you hard disk. 

I will return in a minute to explain how to check if the partition is mounted and how to unmount it &#8212; in case you still want to use the partitioning tool (GParted) on it.

Yes I actually tried to create a partition from the LiveCD before the installation, which I now realized was wrong and I should have just done it through the install. I found info that TestDisk is included in the Ubuntu LiveCD but I can't find it and the terminal says it isn't installed, trying to install it from the terminal with "tar xjf testdisk-6.10.linux26.tar.bz2 comes up with "Cannot open: No such file or directory". Edit: The .tar.bz2 file is on my desktop.

Will this be easier to do if Ubuntu was installed on the partition I made or do I risk losing data if I write on the hard drive now?

Edit: I got Testdisk up and running, it can see the NTFS partition but invalid boot sector. I think I should be able to recover data from it once I learn how to use the program.

---

### Post by Piraja on 2009-01-29
It is safe to install Ubuntu onto the 80 GB unallocated space, making sure you do not touch the NTFS partition. Actually I was mistaken when I asked you to check if the NTFS partition was mounted. You were right in saying that when it's marked with the exclamation mark it cannot really be operated upon. It might be a good idea to read for instance the Psychocats tutorial on partitioning and installing Ubuntu. You can find the link in my sig.

In any case, I do not think that you have really lost the data on your NTFS partition, but I'm not sure how to proceed in order to retrieve it.

Below you can see an example of a dual boot partitioning, a screenshot of GParted on my laptop.

[P.S. And another one in which you can see the mount-points too, showing that I have a separate /home partition, which is a good idea to make &#8212; but that's not urgent for you at this point. Welcome to Ubuntu and good luck, with a little patience everything will work out just fine.]

---

### Post by -kg- on 2009-01-29
I would wait for caljohnsmith before I did much of anything.

You might be able to glean some information out of [this thread.]("http://ubuntuforums.org/showthread.php?p=6620954#post6620954")  Don't pay attention to me...pay attention to caljohnsmith.

:D

---

### Post by caljohnsmith on 2009-01-29
Icy9999, would you please post the output of the following:
```
sudo fdisk -lu
sudo blkid -c /dev/null
```
And for whichever is your Windows partition, try:
```
sudo xxd -s 128 -l 2 -p /dev/[COLOR="Blue"]sda1[/COLOR]
sudo mount /dev/[COLOR="Blue"]sda1[/COLOR] /mnt && ls -l /mnt

```
But replace sda1 with your Windows partition, and please post the output.

[QUOTE=-kg-]I would wait for caljohnsmith before I did much of anything.

You might be able to glean some information out of this thread. Don't pay attention to me...pay attention to caljohnsmith.[/QUOTE]
Thanks for the vote of confidence, I hope I can help. :)

---

