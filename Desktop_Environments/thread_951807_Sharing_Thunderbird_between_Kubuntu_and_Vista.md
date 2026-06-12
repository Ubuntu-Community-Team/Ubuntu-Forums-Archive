---
title: "Sharing Thunderbird between Kubuntu and Vista"
date: 2008-10-18
forum: Desktop Environments
---

### Post by odin_69_ on 2008-10-18
Hello, I am new to Linux and encountered some problems sharing TB between Kubuntu and Vista. Both OS are on my Laptop which is setup as dual boot. I installed TB in Vista and in Kubuntu and I created a NTFS partition SHARE where I put the profile and the Local FOlder so that my mail can be shared. My problem now, when I mount the partition manually the owner of the partition would be me (as in USER) and everything works fine, but if I use the automount the owner of the partition is root and TB cannot read the emails, only the folders. Is there any chance to change the owner of the partition automatically when using the automount? I am not completely positive that this would be the solution to my problem but so far it is my best guess. 

THX so much in advance

---

### Post by odin_69_ on 2008-10-19
The content of my fstab is listed in the following:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=371b1645-bb8c-47f0-8554-e7d407c5a061 / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda6
UUID=2e2fc1d5-ceab-4a63-a50e-d86cadda37a3 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0

/dev/sda4 /home/"USER"/SHARE vfat user,atime,auto 0 0

I think the problem is that thunderbird has not the rights to read out the emails, since the group and the owner are both set to root with the automount.

---

### Post by odin_69_ on 2008-10-21
I think I figured it out, I don't know if this is the smartest way but I specifically listed the user and owner in the fstab file:

/dev/sda4 /home/USER/SHARE vfat users,atime,uid=1000,gid=1000 0 0

thunderbird can now access the files and works quite fine. :-)

---

### Post by SamNSane on 2008-10-21
> **odin_69_ said:**
> I think I figured it out, I don't know if this is the smartest way but I specifically listed the user and owner in the fstab file:

/dev/sda4 /home/USER/SHARE vfat users,atime,uid=1000,gid=1000 0 0

thunderbird can now access the files and works quite fine. :-)

I'm glad to see someone else who isn't afraid to talk to him-her-self. Last year, during a short period where I dual-booted, I just solved the Thunderbird profile "sharing" problem by simply copying the files back-and-forth. Not elegant, but at least doable without much hassle.

Thank you for posting this information. I just ran across someone who's doing a dual boot now who needs the information. I was going to just change permissions at the mount point for the NTFS volume in the file system, but figured there were probably other ways of going about it. To tell you the truth, I'm not sure which method I should use, but at least you've provided an alternative I can try if the first attempt doesn't get the job done.

If there's someone passing by this thread who sees that one or the other of us (or both of us) is about to run into problems, please say so!

Thanks again, odin_69_.

---

