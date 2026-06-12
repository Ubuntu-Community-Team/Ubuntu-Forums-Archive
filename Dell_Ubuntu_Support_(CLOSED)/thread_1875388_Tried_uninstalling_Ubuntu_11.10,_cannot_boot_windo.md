---
title: "Tried uninstalling Ubuntu 11.10, cannot boot windows now!"
date: 2011-11-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by conn250 on 2011-11-04
I have a dell inspiron 1545. I deleted the Ubuntu partitions from the computer manager. Now I cannot boot windows 7. When I restart I get the following:

error: no such partition. 
grub rescue>

---

### Post by ronnystickshift on 2011-11-06
the same thing happened to me - what i THINK happened is that you wiped the partition that contained your boot loader (grub) information, so when grub starts it can't find anything.  windows is most certainly still there, the boot loader just can't find it.  i reinstalled ubuntu and used the partition manager manually when i did so, and after that everything worked fine.

if you want to use windows only, once you've gotten grub back you'll have to figure out how to get windows to overwrite the master boot record, which i'm sorry to say i don't know how to do, except to reinstall windows (obviously not an ideal solution) - but i'm sure you can find some windows forum with people to help you do that.

if you want a different version of ubuntu, or different version of linux, once you get grub back and working you can just install the version of linux you want, using the install cd's partition manager to wipe the partition with ubuntu 11.10 on it, reformat it, and install from there.

good luck!

---

### Post by Megaptera on 2011-11-06
Hi conn250,
Using your Windows 7 disc or repair discs, you need to "fix mbr".

Guide here:  [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by linuxaddix on 2011-11-06
its a grub rescue not a mbr rescue.u can get a grub rescue / mbr repair disc here:
[http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download](http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download)
this is directions on how to use it here:
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
basically all you do is burn the iso to a cd
then make sure you have internet connection 
after boot up of disc it will check a few things then ask what you want it to do
select rcommended repair and it repairs your grub. simple and easy

---

### Post by linuxaddix on 2011-11-06
or you can click on the advanced settings and click through the tabs and find repair mbr

---

### Post by bluexrider on 2011-11-06
> **conn250 said:**
> I have a dell inspiron 1545. I deleted the Ubuntu partitions from the computer manager. Now I cannot boot windows 7. When I restart I get the following:

error: no such partition. 
grub rescue>


What do you want to do? 
To use Ubuntu Boot from a Live CD/DVD and reinstall this will also give you access to Windows.
To use Windows 7 you need to fix the MBR

Your choice

---

