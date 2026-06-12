---
title: "Grub install on sdb with RAID 1..."
date: 2006-07-21
forum: Desktop Environments
---

### Post by JCorrea920 on 2006-07-21
I am having a little trouble with my grub loader on my second SATA drive which is an active drive on a RAID 1 array. I have been following the instructions on [this website]("http://users.piuha.net/martti/comp/ubuntu/raid.html") which reads at the bottom:
> 
Finally I reinstalled the boot loader so that the system will boot even if the primary disk (sda) disappears in the future. 

martti@ubuntu:~$ sudo grub-install /dev/sda

martti@ubuntu:~$ sudo grub
grub> device (hd0) /dev/sdb
grub> root (hd0,0)
grub> setup (hd0)
grub> quit


Is this right? Shouldn't it be:

```
grub> device (**[COLOR="red"]hd1[/COLOR]**) /dev/sdb
grub> root (**[COLOR="red"]hd1[/COLOR]**,0)
grub> setup (**[COLOR="Red"]hd1[/COLOR]**)
grub> quit
```

Before I try what I think is right, I would like to know if I am going about it the right way. Feedback is always welcome. Thanks to all who help in advanced.

---

### Post by catlett on 2006-07-21
Grub places a value on 0. So the first drive is 0, the second drive is 1 and so on.
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by JCorrea920 on 2006-07-21
So if I wanted sdb to boot or take over in case sda fails which code would I use? From the website? or My version? What exactly are the differences?

---

### Post by catlett on 2006-07-21
The grub>root (hd0,0)
tells grub where to find it's files. Only a part of grub will be on the mbr, the rest will be in your boot folder (or boot partition if you have one)
So the first entry grub>root (hd0,0) tells grub that is where to find it's files. The next entry tells it to install the setup to the mbr (if you do not  give a value for a partition, grub takes it to mean the mbr i.e. hdo means setup on the mbr of hd0).

The new thing to me is the device line.
```

martti@ubuntu:~$ sudo grub-install /dev/sda
```That is how you install grub to the mbr from the terminal inside ubuntu.
```
martti@ubuntu:~$ sudo grub
grub> device (hd0) /dev/sdb
grub> root (hd0,0)
grub> setup (hd0)
grub> quit 
```That is him entering the grub shell and then issuing a command to tell grub to look to device sdb 
(the device parameter is new to me but this is the grub manuals description)
> 13.2.3 device
— Command: device drive file

    In the grub shell, specify the file file as the actual drive for a bios drive drive. You can use this command to create a disk image, and/or to fix the drives guessed by GRUB when GRUB fails to determine them correctly, like this:

              grub> device (fd0) /floppy-image
              grub> device (hd0) /dev/sd0
         

    This command can be used only in the grub shell (see Invoking the grub shell). I do not know how this is a failsafe for the future. This set of command should have overwritten the grub-install /dev/sda commnad.

Usually the grub shell is used when booting into your system from grub and there is an error.
You can then press C and get the grub shell. You can then issue commands to grub that are different from the menu list.
For instance I install PC BSD and I made the grub entry wrong. When I booted into grub it wouldn't boot to bsd. I got a grub shell and entered the correctg lines and booted to bsd.
This set of commands looks like a way to boot into your system from the grub shell is grub fails to boot.

Just to state what's in the example. He is installing to the device /dev/sda with the command grub-install 
Then he is entering commands in a grub shell that will setup /dev/sdb


I think I know what he is doing. He is setting up grub twice/ On sda with grub-install AND on sdb. But he has to use the grub shell and the device parameter to direct grub to it because otherwise grub will install to the primaries mbr.
Then if the primary fails, sdb can be bootable because grub is setup on it.

So boot into ubuntu and use this set of commands 
```
martti@ubuntu:~$ sudo grub-install /dev/sda

martti@ubuntu:~$ sudo grub
grub> device (hd0) /dev/sdb
grub> root (hd0,0)
grub> setup (hd0)
grub> quit 
``` You will use 0 because the device line is making grub see it as 0. It sounds like it should work but I don't have any personal experience. This is the first time I have seen the device parameter used in the grub shell to make a second grub install.

---

### Post by JCorrea920 on 2006-07-22
So I tried the steps and I have a small problem. These errors follow:

```
$ sudo grub-install /dev/sda

Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
(hd1)   /dev/sdb


$ sudo grub

grub> root (hd0,0)
 Filesystem type is fat, partition type 0x6

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found


```

I don't follow the procedures, because when I type:

```
grub> find /boot/grub/stage1

Error 15: File not found

```

but when I type:

```
grub> find /grub/stage1

(hd0,0)

```

Where do I go from here, I've tried Knoppix with the same results. What to do?  :confused:

---

### Post by catlett on 2006-07-22
Sorry to leave you hanging a bit, I haven't been around. I am surprised by grub not detecting the files. Just for the heck of it, go to your boot folder, then open grub's folder and see if stage 1 is there.
Do you have a boot partition? Grub may be on that. But grub found stage 1 on hd0,0 and you gave grub that parameter with root hd0,0. It doesn't make sense. 
Is grub installed and working? Can you boot into ubuntu with grub?
Here are a couple of links that may help [http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)
[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)
[http://wiki.linuxquestions.org/wiki/GRUB_Howto_and_Trouble-shooter](http://wiki.linuxquestions.org/wiki/GRUB_Howto_and_Trouble-shooter)

---

### Post by JCorrea920 on 2006-07-28
Catlett,

Okay I have been banging my head about a little, but realized that sda1 is Linux RAID and sdb1 is fat16 causing the confusion even though they share the same files on the RAID 1 Array. So I disconnected sdb1 from the array and fdisk the sdb1 partition and changed the filesystem type to Linux RAID and hot added it to the array and we were in business, able to boot from both disks. Thanks you so much for your support. ;-) 
For more info try either:

```
man fdisk
```

```
man mdadm --add
```

---

### Post by catlett on 2006-07-28
> **JCorrea920 said:**
> Catlett,

Okay I have been banging my head about a little, but realized that sda1 is Linux RAID and sdb1 is fat16 causing the confusion even though they share the same files on the RAID 1 Array. So I disconnected sdb1 from the array and fdisk the sdb1 partition and changed the filesystem type to Linux RAID and hot added it to the array and we were in business, able to boot from both disks. Thanks you so much for your support. ;-) 
For more info try either:

```
man fdisk
```

```
man mdadm --add
```

Great! I have a mainboard with sata connectors, I really have to use them. I am going to be a dinosaur if I don't install and use the new technology. Sorry I couldn't help more with the Raid issue but I am glad you posted the end result. I may very well be using your instructions to get my grub to boot after I join the 21st century and set up a Raid array. 
Glad your finally up and running, see you around the forums.

---

