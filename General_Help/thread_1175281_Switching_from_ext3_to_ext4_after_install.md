---
title: "Switching from ext3 to ext4 after install"
date: 2009-06-01
forum: General Help
---

### Post by su-37 on 2009-06-01
Hey. I recently installed ubuntu 9.04 and am loving it. I would like to know how to convert my file system to ext4. I have followed the steps in this web page: [https://help.ubuntu.com/community/ConvertFilesystem](https://help.ubuntu.com/community/ConvertFilesystem) to convert to Ext4 but when i check my file system by typing the second command it still says ext3. Has anyone got any ideas on to to properly convert or what i did wrong?
:popcorn:

---

### Post by DeMus on 2009-06-01
> **su-37 said:**
> Hey. I recently installed ubuntu 9.04 and am loving it. I would like to know how to convert my file system to ext4. I have followed the steps in this web page: [https://help.ubuntu.com/community/ConvertFilesystem](https://help.ubuntu.com/community/ConvertFilesystem) to convert to Ext4 but when i check my file system by typing the second command it still says ext3. Has anyone got any ideas on to to properly convert or what i did wrong?
:popcorn:

What is your Ubuntu disk? Is it, like in the example /dev/sda1 or are you using another disk?
Please use a text editor and open your /etc/fstab file. Copy the contents (ctrl-a, ctrl-c) into your answer (ctrl-v).

You did do step 1? After that you did do a reboot?

Let's wait for your answers first and go from there.

---

### Post by SunnyRabbiera on 2009-06-01
I would not do it, EXT4 is very new and there is the data loss bug.
EXT3 will do fine, there are no security risks by still using EXT3 and its still a viable filesystem.

---

### Post by su-37 on 2009-06-01
Yes my disk was /dev/sda1. and my /etc/fstab is
  GNU nano 2.0.9              File: /etc/fstab                        Modified  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8bba5c26-a291-4d2b-9599-229b5e1ee866 /               ext3    relatime,erro$
# /dev/sda5
UUID=1750a8df-6c37-4cb8-a6c5-c8a70e0fedeb none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

And yes after changing it to ext4 i did reboot.

---

### Post by DeMus on 2009-06-01
> **su-37 said:**
> Yes my disk was /dev/sda1. and my /etc/fstab is
  GNU nano 2.0.9              File: /etc/fstab                        Modified  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8bba5c26-a291-4d2b-9599-229b5e1ee866 /               ext3    relatime,erro$
# /dev/sda5
UUID=1750a8df-6c37-4cb8-a6c5-c8a70e0fedeb none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

And yes after changing it to ext4 i did reboot.

One question:
In your first post you say: "but when i check my file system by typing the second command it still says ext3"
Which command was that? Is the one at Step 2?
What happens when you just follow all the steps written here:


**Step 1: Switch the existing Ext3 file system to the new Ext4 driver**

We will start by switching over to the Kernel's Ext4 driver without changing the existing files on disk. We can do this as the Ext4 driver is backwards compatible and can mount an Ext3 file system.

```
sudo nano /etc/fstab
```

Look for ext3 on the line that defines your disk and change it to ext4. Here's an example of what the file may look like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=327c1819-14e1-4b96-b9d2-d5e55e50f1ae /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=900e39f2-ad49-42ee-a7f5-8e6807d6b35b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

The only change we need to make is to replace ext3 with ext4 for dev/sda1. In case you did a manual partitioning back when you first installed Ubuntu you may have more than one entry with ext3. In that case, change all of them to ext4.

Make a note of the device as you will need it in the next step. In the example above, the device is /dev/sda1.

Next reboot your system. This is required so that you switch to the Ext4 Kernel driver. Do not continue this guide without rebooting first.

**Step 2: Enable Ext4 features**

Now that we're using the Ext4 driver we can enable the Ext4 features. Open a Console and type (replace <dev> with the device noted in the previous step):

```
sudo tune2fs -O extents,uninit_bg,dir_index <dev>
```

For the example above where the device was /dev/sda1 the command would look like this:

```
sudo tune2fs -O extents,uninit_bg,dir_index /dev/sda1
```

The next step is to do another reboot. The reason is that after enabling the Ext4 features it is required to run a file system check which can only be done on an unmounted file system. Of course, unmounting your root file system while the system is running is not so good. Luckily running the tune2fs command above marks the file system as "dirty" and a file system check will be automatically performed at next boot.

Note that when you boot the first time you will see a long list of warnings of file system issues. These can be ignored and are perfectly normal. After the warnings are printed it will run a forced file system check and proceed with the boot.

Once the system comes up you're almost done, you are now running Ext4.

**Step 3: Re-installing GRUB**

If you convert your boot file-system ("/boot") to ext4, and you use the GRUB boot loader, you will need to install a version of GRUB which understands ext4. Your system may boot OK the first time, but when your kernel is upgraded, it will become un-bootable.

To fix this, you can issue the command (replace <dev> with the device noted in the previous step):

```
sudo grub-install <dev>
```

For the example above where the device was /dev/sda1 the command would look like this:

```
sudo grub-install /dev/sda
```

Finally, one thing to note: Only files written after this conversion will take full advantage of Ext4. Existing files will stay with the Ext3 format. What this means on a practical level is that you will not notice much of a speed increase right away, but as files get re-written it will gradually speed up. It's yet another reason to do your Ubuntu updates, as the updates replace files.

---

### Post by Yellow Pasque on 2009-06-01
It doesn't look like you changed it :\
Try:
```
gksudo gedit /etc/fstab
```

---

### Post by Gen2ly on 2009-06-01
First did you do this while the filesystem was unmounted?  Do not try to convert an ext3 filesystem while it ismounted, run from the liveCD and do so.  Second, did you run fsck to fix the nodes afterwords?  Look at the Official wiki to know how to do this:

[Ext4-Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4)

Then edit your fstab to reflect you're using ext4.  E.g. mine is:

```
UUID=3c971fcb-c450-433f-8363-fe816d4773db       /       ext4    defaults        0 1
```

Ah, demus, u beat me. :)

Oh, and don't listen to Sunny, ext4 is a great filesystem.  The data loss he's talking about can happen on power-failures because ext4 writes to disk less often than ext3 for performance values.  This too can be tuned in your fstab.

---

### Post by su-37 on 2009-06-01
> **Temüjin said:**
> It doesn't look like you changed it :\
Try:
```
gksudo gedit /etc/fstab
```

Okay i used this instead of what the page says in order to get to the window where i change to ext4 and from there i did what it said. I have now checked using the code above and it says ext4. Nothing wrong yet i think its solved.:popcorn:

---

### Post by DeMus on 2009-06-01
> **su-37 said:**
> Okay i used this instead of what the page says in order to get to the window where i change to ext4 and from there i did what it said. I have now checked using the code above and it says ext4. Nothing wrong yet i think its solved.:popcorn:

Good, congratulations. One thing though:
existing files on your harddidk will still use the ext3 system. Once they are re-written they will be re-written in ext4, so you'll benefit the advantages from the new system. New files obviously will have them straight away. This means speed increase will take some time to happen.
Have fun computing.

---

### Post by su-37 on 2009-06-01
Yeah i read that on the page. Thanks though. Does anyone have anyother benefits of ext4? Go ubuntu!

---

### Post by vanquishedangel on 2010-07-29
Hi, I know this post is old and not mine lol, but I followed all your instructions and they worked beautifuly in ubuntu licid. I have grub 1.98 and I got a grub command line when I rebooted, so I used my ubuntu 8 disk and reconfigured grub and it seems to be working, I checked grub version and it is still 1.98 ( ubuntu 8 disk has legacy on it) So i dont know what the problem is there or why it kept booting to the command line for grub in the bios.

Also I reinstalled everything after I changed to ext4, would that handle the ext3/ext4 switch? I just went into synaptic and clicked reinstall for everything.

---

### Post by wizarddrummer on 2010-08-12
> **su-37 said:**
> Hey. I recently installed ubuntu 9.04 and am loving it. I would like to know how to convert my file system to ext4. I have followed the steps in this web page: [https://help.ubuntu.com/community/ConvertFilesystem](https://help.ubuntu.com/community/ConvertFilesystem) to convert to Ext4 but when i check my file system by typing the second command it still says ext3. Has anyone got any ideas on to to properly convert or what i did wrong?
:popcorn:

I would caution against ext4.

I mistakenly selected ext4 when I installed and I have had nothing but trouble.

more than one occasion where it flaked.

Used it yesterday, transferred more than 20 GB of files to what I thought was a more secure file system and hard drive only to find out that it crapped all over itself.

The machine (from another thread) failed to boot; when i put in the live cd virtually all of the files that i copied are not there. The folders are there but the data is missing.

BIG mistake; HUGE mistake using ext4 which is so new that there's no dust on it.

I've lost data and if I do this install again, i will use ext3.

---

