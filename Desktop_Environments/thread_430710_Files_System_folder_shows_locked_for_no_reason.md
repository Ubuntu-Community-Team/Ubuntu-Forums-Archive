---
title: "Files System folder shows locked for no reason"
date: 2007-05-02
forum: Desktop Environments
---

### Post by heatpumpcontrol on 2007-05-02
I have all of a sudden noticed two files that appear locked, one in my /home director the other in a ext3 partition located on the same disk.

Here is my scenario:
/dev/hda1ext3 / 9.77gib
/dev/hda2 extended 139.27gib
 /dev/hda5 ext3 /home 67.99gib
 /dev/hda6 ext3 /media/hda6 69.66gib
 /dev/hda7 linux swap 1.62gib

When I click on my Home folder I have a "nm.log" file that is locked and I can not delete it.

When I click on my /hda6 partition (which I use to back up my /home for now until I can get my Fasttrack 2000 array working in Ubuntu), there is all of a sudden a "lost+found" directory which I did not create and can not delete. 

I have noticed that the "File System" directory will show a lock after I click on it. I can view the files but it indicates a lock right away. This does not happen on my laptop. It is not partitioned though. I have one "/" partition and a "swap" partition on it.


Please help.... I like a clean folder and if I can't delete this "lost+found" directory and the "nm.log" file I would like to hideihemt so that I don't have to see them. 

Oh, the 'nm.log' file is empty. I was messing around with my network manager earlier because it would not reconnect after coming out of standby and now this file shows up.

Thank you again..hpc :confused:

---

### Post by vedace on 2007-05-02
Don't delete lost+found/; that is where the filesystem checker places any detached files it finds; it's a standard part of the unix file system.  If you don't want it to appear, don't mount the partition on which the folder appears when you boot the machine.  That way, no filesystem checker will ever run on it, and the directory won't be re-created.  Deleting the log file, however, is probably harmless.  In a terminal, do:
```
cd
sudo chown [YOUR USERNAME] nm.log
sudo chmod 744 nm.log

```

Now the "lock" will be gone, and you'll be able to delete it normally.

---

### Post by heatpumpcontrol on 2007-05-02
> **vedace said:**
> Don't delete lost+found/; that is where the filesystem checker places any detached files it finds; it's a standard part of the unix file system.  If you don't want it to appear, don't mount the partition on which the folder appears when you boot the machine.  That way, no filesystem checker will ever run on it, and the directory won't be re-created.  Deleting the log file, however, is probably harmless.  In a terminal, do:
```
cd
sudo chown [YOUR USERNAME] nm.log
sudo chmod 744 nm.log

```

Now the "lock" will be gone, and you'll be able to delete it normally.

That worked thank you.

Would you happen to know why the System directory shows locked only after I open it? I didn't show that before which coincides when the 'lost+found' icon showed up on the /hda6 partition. 

Hey, how about if I delete the partition and recreate it? I've backed up my files in it already. What do you think?

hpc

---

### Post by vedace on 2007-05-02
Where is the directory you're talking about?  On your root partition?  Or are you talking about a partition for a different OS?  Is "file system" its name, or is that just how you're referring to it?  I'd bet you're talking about the directory for another partition, such as in /mnt/ or /media/.  In this case, the partition is locked because it's being mounted on boot such that only root can access it.  You can change this by modifying /etc/fstab.  DOn't go deleting any partitions, it is entirely unnecessary.

---

### Post by heatpumpcontrol on 2007-05-02
Under 'Places' I click on 'Computer' and the file browser opens and on the left pane I select 'Tree' view. Under my 'Home' directory is the 'File System' directory folder icon. 

After boot up it shows like a normal icon but after I open it, the folder icon on it show a 'lock' on it.

Hope this makes sense.

---

### Post by kerry_s on 2007-05-02
My guess is it's a seperate drive/partion that your actually mounting when you click on it. mounting is done with root privlages and you need root privlages to unmount it. The icon doesn't show till you click on it which mounts it to make it available. Does that make since? Sorry still early and i'm not awake yet.

---

### Post by heatpumpcontrol on 2007-05-02
OK that makes sense. So when I click it I mount it telling me that I only have read acces. OK I'll accept that.

Thanks that makes sense.

Would you happen to know how to install or reinstall xserver.xorg?  My laptop has gone down and when I try to reconfigue xserver it says it's not installed. I am running Beryl.

Thanks again.

---

### Post by kerry_s on 2007-05-02
sudo apt-get install xorg

Should get you all the X applications, it's what i use for my minimal installs.

---

### Post by heatpumpcontrol on 2007-05-04
thanks, I ended up redoing my laptop with two partitions this time. Just starting out so it's all new to me. I like Linux though especially the deb version. I find the kde looks too much like windows and I want to get away from that look though I'm surrounded by them at work.
LOL

---

