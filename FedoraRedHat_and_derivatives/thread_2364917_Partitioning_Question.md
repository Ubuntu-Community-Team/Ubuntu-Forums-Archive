---
title: "Partitioning Question"
date: 2017-06-29
forum: Fedora/RedHat and derivatives
---

### Post by RobGoss on 2017-06-29
Hello everyone, So I have fedora 25 installed on one of my machines, what I'm trying to do is free up some space for another os

I tried using Gparted  but I'm unable to make any unallocated space what I'm I doing wrong?

Each time I try everything is grayed out and can not use the resize option 

I'm aware I have to unmount the current os in order to create a new unallocated partition, but for some reason it's not working

Thanks for any help with this

---

### Post by QIII on 2017-06-29
Hello!

If you did a default installation, Fedora uses LVM.  That makes using something like Gparted a bit dicey ... well, nigh impossible.

[This]("https://docs.fedoraproject.org/en-US/Fedora/14/html/Storage_Administration_Guide/ch-lvm.html") has some good info specific to Fedora.

Cheers!

---

### Post by RobGoss on 2017-06-29
Yes I noticed the Fedora partition was LVM, I'm not use to working with them. The link you posted is that a tool to Handel the LVM partitions?

---

### Post by QIII on 2017-06-29
LVM management tasks.  See "Editing a Logical Volume" specifically.

That particular link is in the Fedora 14 tab, but that is the most recent I see.  LVM has been pretty static, so like using gparted the tools should be the same.

Too busy right now, but I can find some more info on how to do it via the terminal later.

Edit -- Ah.  Always trust Arch to have the [answers]("https://wiki.archlinux.org/index.php/LVM") when it comes to using the command line!

---

### Post by RobGoss on 2017-06-29
Thanks Qlll I'll get it all sorted out

---

### Post by QIII on 2017-06-29
Ask all the questions you need to.  Arch's documentation is often so thorough that it makes you dizzy!

---

### Post by Dennis N on 2017-06-29
If Fedora is on an LVM partition, then may be room on the same partition for your new OS as well as an LVM install, provided it's installer is LVM aware (Ubuntu is). No need to resize anything. Run the command **sudo vgdisplay** in the Fedora terminal to see available space.

---

### Post by QIII on 2017-06-29
Derp.  Got so tied up in "resize LVM" that I didn't consider that if one does manual partitioning a new volume can be created.

---

### Post by RobGoss on 2017-06-29
> **Dennis N said:**
> If Fedora is on an LVM partition, then may be room on the same partition for your new OS as well as an LVM install, provided it's installer is LVM aware (Ubuntu is). No need to resize anything. Run the command **sudo vgdisplay** in the Fedora terminal to see available space.

There's only one os on this machine and that's Fedora, and yes the partition is LVM

---

### Post by Dennis N on 2017-06-29
> **RobGoss said:**
> There's only one os on this machine and that's Fedora, and yes the partition is LVM

So, do you want to stick with LVM and install the new OS as LVM? If so, that will depend on what the new OS is (some installers won't install to LVM), and how much space you have. Run **sudo vgdisplay** in terminal to find free space. If there is free space, you don't need to resize anything. Ubuntu will install to an LVM logical volume.

If you don't want LVM, then you do have to resize Fedora and the partition itself.

---

### Post by RobGoss on 2017-06-29
> So, do you want to stick with LVM and install the new OS as LVM? 

If it can be done I don't really mind as long as I can get both OS's to dual boot. The other OS I'm trying to install is [https://antergos.com/try-it/](https://antergos.com/try-it/) not sure how it will play with fedora

I have plenty of space for the new OS as well


> If you don't want LVM, then you do have to resize Fedora and the partition itself  

This might be a better option do to the fact I don't really work with LVM

---

### Post by #&amp;thj^% on 2017-06-29
> **RobGoss said:**
> If it can be done I don't really mind as long as I can get both OS's to dual boot. The other OS I'm trying to install is [https://antergos.com/try-it/](https://antergos.com/try-it/) **_[U]not sure how it will play with fedora_[/U]**


If I may make a personal suggestion...if you do install antergos let it handle grub. Have a look here: [https://bbs.archlinux.org/viewtopic.php?id=97121](https://bbs.archlinux.org/viewtopic.php?id=97121) and Here: [https://bbs.archlinux.org/viewtopic.php?id=141409](https://bbs.archlinux.org/viewtopic.php?id=141409) for some tips.
And I have no personal experience with LVM so i also don't know how that will play out.:)

---

### Post by Dennis N on 2017-06-29
> I tried using Gparted but I'm unable to make any unallocated space what I'm I doing wrong?

Is Fedora on a logical partition inside an extended partition? That's a common setup for whole disk install. In that case, you need to unmount two partitions, the logical (Fedora LVM) and the extended partition.

I am not acquainted with antergos, so can't say if it would install to an LVM volume you prepare for it on that LVM partition you have. I see the distro has a forum, maybe you could ask there. Or you may want to go ahead and try and see.

I could not duplicate your resize problem. My LVM partitions are on GPT partitioning, and nothing was greyed out or disallowed when trying to resize with gparted. Although I did not actually do it, I believe I could have. In my somewhat limited LVM experience, I never needed to resize an LVM physical partition, so there may be risks to the data involved when shrinking it. May be best to back up any important data first if you do try it.

---

### Post by RobGoss on 2017-06-30
I do not see any extended partition in Fedora, as far as shrinking the Fedora partition I don't see any option to do that

When I try to install the new OS there's a few options but I'm not familiar with then so I'm uncertain how to proceed

---

### Post by oldfred on 2017-06-30
You cannot look at partitions with gparted or standard partition tools.
LVM has /boot and main LVM which normally is rest of drive. IF UEFI then it also has an ESP - efi system partition.
So you probably do not have a logical partition since with BIOS/MBR it only uses two physical partitions. Then all the rest of the partitions you want are inside the lvm. 

Some that multiple boot do not install using LVM for those systems that default to LVM type partitioning.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

---

### Post by RobGoss on 2017-06-30
Hi Oldfred, thanks so much for the info

So are you saying the dual for LVM is not possible or just very difficult to setup?

When I look at the LVM partition there's not really much there, I don't see any swap or anything

---

### Post by Dennis N on 2017-06-30
The LVM install into an existing LVM physical partition is not difficult. That's how I did mine. The pre-install setup amounts to two terminal commands. If you would care to post the output of

```
sudo vgdisplay
```

run from Fedora, we get the necessary specific information. Then those commands can be formulated.

---

### Post by RobGoss on 2017-06-30
Thanks Dennis N, I'll post the output for that command as soon as I'm at my desktop

---

### Post by RobGoss on 2017-06-30
Here goes the results from running that command:

**sudo vgdisplay**

```
 --- Volume group ---
  VG Name               fedora
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                3
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               <297.09 GiB
  PE Size               4.00 MiB
  Total PE              76054
  Alloc PE / Size       76054 / <297.09 GiB
  Free  PE / Size       0 / 0   
  VG UUID               ZCsQDi-u5Yz-BWzk-FwIb-wpfa-l1ol-7xhZuc
```

---

### Post by Dennis N on 2017-06-30
Making progress! We now know the name of the volume group (vg): fedora
We also know:
The size of the vg is about 300 gB
The vg occupies all of the partition, since free space is 0.

All that is not surprising.

Almost done. Next to find out how much space Fedora has been allocated within the vg, please run **sudo lvs** and post the result. 

In the meantime, here is a guide for Ubuntu that explains some LVM basics. I used it when I was learning about this topic. It all applies to other distros too. You might want to look it over, since your existing Fedora is LVM. The information might come in handy.
 
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

### Post by RobGoss on 2017-07-01
Thanks for the link Dennis, here you go

```
$ sudo lvs
  LV   VG     Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home fedora -wi-a----- <241.27g                                                    
  root fedora -wi-a-----   50.00g                                                    
  swap fedora -wi-a-----    5.82g                                                    

```

---

### Post by Dennis N on 2017-07-01
Fedora has taken all the space for itself. It would be necessary to resize **home** to make room for another OS.

I suggest first finding how much of **home** is used. Run from Fedora terminal and post the output of:

```
df -h | grep home
```

---

### Post by RobGoss on 2017-07-01
That command does not return anything for some reason

---

### Post by Dennis N on 2017-07-01
> **RobGoss said:**
> That command does not return anything for some reason

That's strange. Output should show any mounted file system containing the string "home". Please run it without the grep part:

```
df -h
```

The output is information on all the mounted partitions and devices, including the LVM logical volumes, and should inform us how much of it is available to be reduced in size.

---

### Post by RobGoss on 2017-07-01
This is what I got after running **df -h**

```
Filesystem      Size  Used Avail Use% Mounted on
dev             2.9G     0  2.9G   0% /dev
run             2.9G   35M  2.9G   2% /run
/dev/sdf1       1.8G  1.8G     0 100% /run/archiso/bootmnt
cowspace        320M   67M  254M  21% /run/archiso/cowspace
/dev/loop0      1.7G  1.7G     0 100% /run/archiso/sfs/root-image
root-image      320M   67M  254M  21% /
tmpfs           2.9G     0  2.9G   0% /dev/shm
tmpfs           2.9G     0  2.9G   0% /sys/fs/cgroup
tmpfs           2.9G  6.1M  2.9G   1% /tmp
tmpfs           584M   40K  584M   1% /run/user/1000
```

---

### Post by Dennis N on 2017-07-01
Well, that's a puzzle. I don't see any sign of this output being from Fedora LVM installation.

For example, we should see a separate boot partition outside the LVM partition and it isn't shown. We should see the root partition on an LVM logical volume, as seen in post #21. LVM volumes would start with: 

**[FONT=Courier New]/dev/mapper/... [/FONT]**

in the df -h display.
 
For comparison, here is the output from my LVM install of Xubuntu:

```
dmn@Kayleigh:~$ df -h
Filesystem                          Size  Used Avail Use% Mounted on
udev                                984M     0  984M   0% /dev
tmpfs                               201M  6.4M  195M   4% /run
/dev/mapper/common_vg-xubuntu_1604   15G  6.2G  7.8G  45% /
tmpfs                              1003M  220K 1003M   1% /dev/shm
tmpfs                               5.0M  4.0K  5.0M   1% /run/lock
tmpfs                              1003M     0 1003M   0% /sys/fs/cgroup
/dev/sdb8                           380M  252M  104M  71% /boot
/dev/mapper/common_vg-files          30G   16G   13G  55% /mnt/files
tmpfs                               201M  4.0K  201M   1% /run/user/108
tmpfs                               201M   44K  201M   1% /run/user/1000

```
In the Filesystem column, note the LVM logical volume mounted on / and the regular partition /dev/sdb8 mounted on /boot.

You need to figure out what you are doing wrong. Did you boot an ISO (isoboot?) instead of a regular boot of Fedora? Loop mount (/dev/loop0)? I am confused at the moment.

---

### Post by RobGoss on 2017-07-01
Sorry Dennis I was booting from the new live OS here is the output from that command


```
 Filesystem               Size  Used Avail Use% Mounted on
devtmpfs                 2.9G     0  2.9G   0% /dev
tmpfs                    2.9G     0  2.9G   0% /dev/shm
tmpfs                    2.9G  1.4M  2.9G   1% /run
tmpfs                    2.9G     0  2.9G   0% /sys/fs/cgroup
/dev/mapper/fedora-root   50G  7.2G   40G  16% /
tmpfs                    2.9G   76K  2.9G   1% /tmp
/dev/sda1                976M  175M  735M  20% /boot
/dev/mapper/fedora-home  238G  562M  225G   1% /home
tmpfs                    583M   28K  583M   1% /run/user/42
tmpfs                    583M   40K  583M   1% /run/user/1000

```

---

### Post by Dennis N on 2017-07-01
> **RobGoss said:**
> Sorry Dennis I was booting from the new live OS here is the output from that command


```
 Filesystem               Size  Used Avail Use% Mounted on
devtmpfs                 2.9G     0  2.9G   0% /dev
tmpfs                    2.9G     0  2.9G   0% /dev/shm
tmpfs                    2.9G  1.4M  2.9G   1% /run
tmpfs                    2.9G     0  2.9G   0% /sys/fs/cgroup
/dev/mapper/fedora-root   50G  7.2G   40G  16% /
tmpfs                    2.9G   76K  2.9G   1% /tmp
/dev/sda1                976M  175M  735M  20% /boot
/dev/mapper/fedora-home  238G  562M  225G   1% /home
tmpfs                    583M   28K  583M   1% /run/user/42
tmpfs                    583M   40K  583M   1% /run/user/1000

```

That looks better. home is about 240 gB, now using less than 1 gB, so you should be able to free 200 gB leaving about 40 gB for your Fedora home. O.K?

Need output of **sudo lvdisplay** in order to proceed. Please post.

---

### Post by RobGoss on 2017-07-01
```
   --- Logical volume ---
  LV Path                /dev/fedora/swap
  LV Name                swap
  VG Name                fedora
  LV UUID                AP454m-2HOj-hfpY-xYFw-KFCh-4okv-YT1oEc
  LV Write Access        read/write
  LV Creation host, time localhost-live, 2016-12-24 14:25:19 -0500
  LV Status              available
  # open                 2
  LV Size                5.82 GiB
  Current LE             1490
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
   
  --- Logical volume ---
  LV Path                /dev/fedora/home
  LV Name                home
  VG Name                fedora
  LV UUID                dvp1nJ-pKUo-Au9h-kmSA-z3Qb-OMeD-8SXgHr
  LV Write Access        read/write
  LV Creation host, time localhost-live, 2016-12-24 14:25:19 -0500
  LV Status              available
  # open                 1
  LV Size                241.27 GiB
  Current LE             61764
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:2
   
  --- Logical volume ---
  LV Path                /dev/fedora/root
  LV Name                root
  VG Name                fedora
  LV UUID                KlCK71-rek3-NFYD-Zbes-aKOb-nCAE-OePwc3
  LV Write Access        read/write
  LV Creation host, time localhost-live, 2016-12-24 14:26:08 -0500
  LV Status              available
  # open                 1
  LV Size                50.00 GiB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   

```

---

### Post by Dennis N on 2017-07-01
Ready to resize?

You should have a back up of any important data. There is always a risk of accidental data loss when resizing. 

According to the Ubuntu LVM guide: the LV you are resizing has to be unmounted, so you need run the command from live media with lvm2 package installed. Suggested: Xubuntu or Fedora live media. Live media file manager would display icons for the LVM volumes, but don't click to mount any (no telling what they might be named - an LVM test volume on this computer seen from another OS is just labeled "13 GB Volume"). 

You might want to run **sudo lvdisplay** from the live media's terminal just to test that the LVM commands are working. 

Now to resize: running this in the (live media) terminal will reduce home to 40 gB:

```
sudo lvreduce --resizefs --size 40G /dev/fedora/home
```


Next step: create new LV for new OS.

---

### Post by RobGoss on 2017-07-02
Thank you so much Dennis N, for sticking with me on this much appreciated I'll see what I can do now to resize it....

---

### Post by Dennis N on 2017-07-03
> **RobGoss said:**
> Thank you so much Dennis N, for sticking with me on this much appreciated I'll see what I can do now to resize it....

Glad to be of help. Post back if there are any further problems. I did look at the antergos installer, and it does recognize LVM logical volumes as installation targets.

---

### Post by Dennis N on 2017-07-04
There is a bit more to do after resizing the partition in post #30. Did you use the guide to make the LV for installation?

---

### Post by RobGoss on 2017-07-06
Yes I did and everything worked out as it should thanks so much for your help Dennis N, much appreciated

---

### Post by Dennis N on 2017-07-06
> **RobGoss said:**
> Yes I did and everything worked out as it should thanks so much for your help Dennis N, much appreciated

How did you antergos install go? I planned to install it to test it out and see what all the fuss was about, but the installer would not proceed unless I had a /boot partition defined, and this was on an older BIOS computer. Knowing that should not be necessary, I aborted the whole thing. Image attached of the no-go point.

---

### Post by RobGoss on 2017-07-06
Things were working OK until I posted saying everything went well then I started having problems with error messages and the system would not boot, I had a smaller Hard drive laying around for the same machine so I piggie backed then both and installed the new OS on there.. The LVM partitions don't play well

---

