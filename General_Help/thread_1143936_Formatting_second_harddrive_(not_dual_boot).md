---
title: "Formatting second harddrive (not dual boot)"
date: 2009-04-30
forum: General Help
---

### Post by josh1988 on 2009-04-30
HI every one, I already know this question has been asked a thousand times before, but I am having no luck in figuring out how to properly format my secondary hard drive on my desktop so that I can use to store extra data ie: music,video,photo files. But i do not want to be limited to the fat32 short comings of certain file sizes.

Ok so my first hard drive has Ubuntu loaded on it running perfectly it is a pleasant alternative to xp.

What i would like to know is how to format my second hard drive and mount it so that it automatically loads in my computer

Please be as specific as possible with the instruction I am a complete newbie when it comes to the Linux distros.

Thanks you in advance for any and all help...

---

### Post by Grenage on 2009-04-30
Ok let's try this:

Sudo fdisk /dev/sdc (or whatever drive).
P to check for existing partitions and D to delete any that exist.
N for a new partition.
P for primary partition.
Press return for the next few options (defaults are fine).
T for partition type.
Type 83 then press return.
W for write and exit.

mkfs.ext3 -b 4096 /dev/hdc1 (or whatever the new partition is)

Create a mount point (/mnt/drive2) or whatever: sudo mkdir /mnt/drive2.

vim /etc/fstab to make changes for auto-mounting the drive at boot.
Add the following line, changing hdc1 for your drive partition and drive2 for your mount point name.

/dev/hdc1               /mnt/drive2                     ext3    defaults        1 1

Read and run fstab, then check to make sure it's mounted ok.  You'll get an error back if there was a problem:

mount -a

---

### Post by josh1988 on 2009-04-30
Ok thank you very much i shall try what you suggested when I return home tonight

---

### Post by josh1988 on 2009-04-30
Thank you so much my second hard drive is now formatted and fully functional thank you:P

---

### Post by Monotoko on 2009-04-30
I will however warn you that drive will not mount on any Windows systems, because of the filesystem (ext3 cant be read by windows) just so you dont run into problems if you ever plug it into a windows machine.

---

### Post by Grenage on 2009-04-30
I hope you get on ok, please let me know if you encounter any problems :)

Edit: Ah you posted your success whilst I was idle!  Glad to hear it went well.

---

### Post by josh1988 on 2009-05-01
Ok very sorry it seems I may have jumped the gun a little early on assuming every thing was correct.
I though just because i could see the drive now it would work. Wrong.
How can i add read and write access to the extra drive now? (if it is possible)...

Thanks again sorry for the inconvenience.

---

### Post by Grenage on 2009-05-02
Hello again :)

After formatting the drive, did you go through the process of mounting it?  If you look at my example above, you will see I mounted to /mnt/drive2.  What that means is that anything I put in /mnt/drive2 gets written to the drive.  You could make a shortcut/link from there to your desktop if you so wished:

ln -s /mnt/drive2 ~/Desktop/seconddrive

seconddrive is merely the name the link will have.

---

### Post by fualad on 2009-05-02
If you need ext3 on windows theres [Ext2 IFS]("http://www.fs-driver.org/")

---

### Post by josh1988 on 2009-05-06
Ahh sorry for the delay been away for a few days,
And thank you very much i managed to get every working read and write access..
Thanks for everything :D

---

### Post by rkymtndave on 2009-05-09
i've been following your instructions here but I keep getting an error of invalid block size or invalid blocks count after mkfs ext3 -b 4096/dev/sdb1
What am i doing wrong? or how do I find out what the proper block size os supposed to be? thanks

---

### Post by Marko723 on 2009-05-22
Thanks for all the information in this thread.  I was successful in mounting a second drive on my system.  I even managed to change the icon on the desktop link to a picture of a hard drive  :D

I have a request.  I'd like this drive to show up in my computer file browser main window (from the desktop menu select "Places-> Computer")  Currently there is the boot drive "filesystem" icon.  I'd like to add another drive Icon linked to this second drive I just installed.  

I did manage to have it show up on the left side bar as a folder icon under "places", but not in the main window.   I've poked around the forums, but not having much luck in tracking something down.

Thanks

Mark

---

