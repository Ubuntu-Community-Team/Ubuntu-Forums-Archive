---
title: "Code to mount a second drive at bootup?"
date: 2009-06-19
forum: General Help
---

### Post by suchin on 2009-06-19
What is the proper code to get a second drive, Gparted and formatted via ubuntu 9.04, to mount when you boot up?

Suchin

---

### Post by akakingess on 2009-06-19
> **suchin said:**
> What is the proper code to get a second drive, Gparted and formatted via ubuntu 9.04, to mount when you boot up?

Suchin
I believe you edit mtab (or it might be fstab) I can't quite remember, but you add a line to mtab with the device you want to mount (/media/sda2 for example) to the bottom and save, keep in mind to edit it you need to open with "sudo gedit etc/mtab" and enter your password. Don't take my word for it, you can open both files or try to and see which one it is, but that is how I've done it in the past.

akakingess

---

### Post by monkey56657 on 2009-06-20
Hello. 

You can mount devices using this:

$ mount -t <type> /dev/<name> /path/to/folder

Basically the command breaks down like this:

**mount** - the command used to mount any storage device. 
**-t** - specifies that you are providing the devices formatting type. 
**<type>** - the devices format type (for example: ext3)
**/dev/<name>** - the name of the device to mount (for example /dev/sda1)
**/path/to/folder** - the full path to a folder on your system where the drive should be mounted. 

You can also add the device to your /etc/fstab file and it will automatically be mounted on startup. 

[http://wiki.linuxquestions.org/wiki/Fstab](http://wiki.linuxquestions.org/wiki/Fstab)
[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

Regards, Jonathan

---

### Post by cariboo on 2009-06-20
Just something that bugs me a bit, you don't need to code anything to mount a second drive at bootup. You just have a to add a simple line of text to /etc/fstab. Have a look at this [page]("https://help.ubuntu.com/community/Fstab"), it will explain how /etc/fstab works,

You can add a drive using either the device label or uuid. This is a device label example:

```
/dev/sda3	/media/movies	xfs	relatime	0	2
```

[list]
[*] /dev/sda3 is the device label
[*] /media/movies is the mount point
[*] xfs is the file system, you should probably use ext3
[*] relatime as default for linux native file systems. You can find a discussion of relatime here : [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)
[*] 0 = don't dump
[*] 2 = Check this partition next
[/list]

This is an example of mounting by uuid:

```
UUID=7911a1c9-3c28-4a63-80c7-9cb6607b81eb /home/storage	ext4	relatime	0 0
```

Every thing els is the same as using the device label

---

### Post by suchin on 2009-06-20
Thanks for answers. But ...

Please see what I have done wrong here then, Ubuntu bootup time is @ 15 min, and getting a second slave drive to start takes @ 2-3 min. It works every time but that is the times it take.  After my ex boyfriend put Ubuntu on my laptop that XP crashed a year ago (the only good thing he ever did)  I have learned to do a few things and begun to like Ubuntu, but  I'm still green on Linux.

 I'm home from school and decided to wipe my home computer an Asus A8S-X series that I  build with my sister a while back and installed 9.04 on it as well. I Dban 2 ide drives. Plugged one in (1) as a master and installed Jaunty & updates, boots fine. Unplugged (1) Took the second drive (2) and choose cable select installed Jaunty & updates, boots fine. Now I put the master (1) first on the cable and (2) on the second spot. Boots fine every time but takes forever.
 
 Unplugging and just running one drive, either one and it boots in a flash. This is code I used to install my slave drive:

sudo mkdir sdb1
sudo mount /dev/sdb1 /media/sdb1
sudo nano /etc/fstab /dev/sdb1 /media/sdb1 ext3 defaults 0 0
 
I'm sure there is a thread exactly on how to do this all but I couldn't find it.

Suchin

---

### Post by akakingess on 2009-06-20
Is there a reason that you installed Jaunty on both drives, rather than just install on one and then format the other ext3 for storage? That could be part of the problem, I'm not sure as I am farely new to linux, too. And thanks cariboo907 for the clarification, I thought it was much easier to just add a single line than do all the other stuff, just didn't know if I had answered the question correctly (I guess I still messed up confusing mtab & fstab, but I tried to help).

akakingess

---

### Post by suchin on 2009-06-20
I tried after Dban to format the the slave drive but I could never get it to show up. Do you think I should try to do that now since now it shows up? In that case exactly how?

Take your time, I'm going to bed it's late for me. I look for any answer tomorrow.

Suchin

---

### Post by akakingess on 2009-06-20
> **suchin said:**
> I tried after Dban to format the the slave drive but I could never get it to show up. Do you think I should try to do that now since now it shows up? In that case exactly how?

Take your time, I'm going to bed it's late for me. I look for any answer tomorrow.

Suchin
Yeah, now that it shows up I might try with Gparted to reformat it and just use it strictly as storage rather than have a second bootable drive.  Just my opinion, I'm sure others may say differently and I hope they do, as I am learning right along with you.

akakingess

---

### Post by suchin on 2009-06-20
Hi

Ok, so I was stupid to turn of my computer last night. Now it will not boot up with both drive on today. So I unhooked my master took my slave and Dbanned it, Gparted it. Plugged the master (yes changed the bios)and this drive back in as a slave. Rebooted and there it just sits... must have given it some bad karma?

Anyone like to give this a whirl here or somewhere else? I really can't spend much more time on this. I know I can format it as a windows drive and Ubunto will probably see it in the end, and then I could use it that way. But it just bugs me that I could not do it.

Suchin

---

