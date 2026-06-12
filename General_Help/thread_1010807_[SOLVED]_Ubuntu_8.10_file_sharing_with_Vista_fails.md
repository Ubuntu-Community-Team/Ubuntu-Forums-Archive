---
title: "[SOLVED] Ubuntu 8.10 file sharing with Vista fails"
date: 2008-12-14
forum: General Help
---

### Post by zuheyr on 2008-12-14
Hello,

I am using dual boot Ubuntu 8.10 and Vista.

I followed the instructions in this excellent link to share a file with Vista (which seems to work for many people):

[http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/](http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/)

I created a folder I want to share on the Ubuntu desktop. When I modify the sharing options, I check the box to allow the other people to write in this folder, it is not saved when I log out.

When I go to Vista, it does not find my computer, when I try the command \\zuheyr-desktop (the name of my ubuntu machine) to create a shortcut Vista does not find it.

I would appreciate any help.

Thanks for reading. Regards, Zuheyr

---

### Post by cb951303 on 2008-12-14
Well this guide is for network sharing meaning two different computers: one with ubuntu and another with vista :D If I understand correctly what you are trying to do is to share files between to OSs in the same machine? If so vista is not capable of seeing linux partitions. I don't know if there is a solution for that.

---

### Post by SteveDee on 2008-12-14
As Linux can see windows folders, saving any files you want to share in a Windows folder should make them accessible to both Windows & Ubuntu.

---

### Post by zuheyr on 2008-12-18
Hello,

Thank you for your replies.

I am sorry for my late reply, I have forgotten check the immediate notification box, so I thought there was no answer.

Maybe I am completely confusing the issue but what I wanted was to be able to store from Windows directly into the Linux file system.

The reason for this is I allocated quite small space for Windows and I only use windows for, say, burning DVD's, music etc. Large files. I wanted to write them directly on a directory which is actually stored in the Linux file system.

I hope I am clear.

Many thanks for reading, best wishes, Merry Christmas,
Zuheyr

---

### Post by cb951303 on 2008-12-18
> **zuheyr said:**
> what I wanted was to be able to store from Windows directly into the Linux file system.


unfortunately you can't. windows doesn't support any filesystem other than FAT and NTFS. Ubuntu uses EXT3 by default.

---

### Post by Cl0ud9 on 2008-12-18
You could create a partition solely for storing files and format it as fat32 so both Ubuntu and Windows can read and write from it.

---

### Post by zuheyr on 2008-12-18
Thank you. 

If I buy an external hard disk with USB, format it FAT32. When I plug it in, then I think both Ubuntu and Vista will automatically see it? This would solve my problem. 

Thank you very much for your prompt responses.

Regards, Zuheyr

---

### Post by cybrsaylr on 2008-12-18
I have an external HDD using NTFS and have been sharing files between Ubuntu, OpenSUSE, XP and Vista for a couple years now with no problems. Ubuntu has no problem reading what's on the Windows partitions but Windows treats the Ubuntu partition as 'unknown' and won't let me see linux files.

There is an app that will allow Windows to go into Ubuntu and read linux files but don't recall what it is.

---

### Post by zuheyr on 2008-12-18
Thank you. 

Let's hope somebody will recall the name of the apt.

When I think of it, a USB stick is FAT32 formatted, is it not? And both Vista and Ubuntu read it. So external storage should be ok, of course, very slow to write to.

Many thanks again,  Regards, Zuheyr

---

### Post by cb951303 on 2008-12-18
> **zuheyr said:**
> Thank you. 

Let's hope somebody will recall the name of the apt.

When I think of it, a USB stick is FAT32 formatted, is it not? And both Vista and Ubuntu read it. So external storage should be ok, of course, very slow to write to.

Many thanks again,  Regards, Zuheyr

Ubuntu should already see your windows vista (NTFS) partition so a FAT32 formatted hdd has no advantage.

---

### Post by zuheyr on 2008-12-18
Yes, in fact the last thing I would like to do is to format a 1TB disk in FAT32, I would want to do NTFS. But can Ubuntu write on a disk formatted NTFS?

Thank you, regards, Zuheyr

---

### Post by jerome1232 on 2008-12-18
> **zuheyr said:**
> Yes, in fact the last thing I would like to do is to format a 1TB disk in FAT32, I would want to do NTFS. But can Ubuntu write on a disk formatted NTFS?

Thank you, regards, Zuheyr

Yes in fact it can; Out of the box no additional software required.

---

### Post by zuheyr on 2008-12-18
That is it, thank you, then I have it. SOLVED. 
Thank you indeed, I learned a lot from this thread.

Again best Season's Greetings! Regards, Zuheyr

---

### Post by arcanus on 2008-12-18
You could use the Thread Tools -> Mark as solved to let people see the status of the issue in the topic of the thread ;)

Glad it worked out tho, and the app that lets you read EXT2/3 file systems on a windows XP OS, is called Ext2 IFS and is available [here]("http://www.fs-driver.org/") Not sure about vista tho...

Magne

---

### Post by zuheyr on 2008-12-18
Hi thank you Magne,

I just did it. I was not aware of such a tool really. Thank you.
I will try that apt tonight. Regards, Zuheyr

---

