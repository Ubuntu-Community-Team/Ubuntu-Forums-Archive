---
title: "Editing GRUB to boot from Flash Drive"
date: 2009-05-19
forum: General Help
---

### Post by papasmurf6768 on 2009-05-19
Hello everyone!  Alright here's my problem.

What I want to do is edit my GRUB boot loader that is ON MY FLASH DRIVE. (Not hard drive.)  I want to edit it to be able to dual boot off the same flash drive.  Here's what I did, succesfully and still attempting to do.

1. Install GRUB to flash drive (I installed it to sdb1.  Tell me if it should be sbd2)-Success
2. Split 2GB flash drive into two 1GB partitions-Success
3. Install Ubuntu 9.04 to first partition (sdb1)-Success
4. Install Kubuntu 9.04 to second partition (sdb2)-Success
5. Configure GRUB menu.lst to be able to boot from both partitions-Needs to be done.

As you can see, all I need to do is get GRUB to boot from both my flash drive partitions.  When I plug my flash drive in and turn on my computer, I get the GRUB menu off of my flash drive.  (I know it's off the flash drive because I edited the titles of my menu.lst, and that's what shows up when I turn on the computer.)  But when I choose either options I typed, it boots off the hard drive, because I copied the boot/grub file from my HD.  So basically, I need to edit my settings to boot from my sdb1 partition, and sdb2 partition.  I know you guys can get this for me, you always pull through for me.  Thanks in advance.  If you need any more info, just ask.  Thanks a lot.

---

### Post by papasmurf6768 on 2009-05-20
UPDATE:

I INSTALLED GRUB TO MY MEMORY STICK, AND IT BOOTED FROM THAT.  THEN I INSTALLED UBUNTU TO THE SAME PARTITION, AND KUBUNTU TO THE SECOND, AND WHEN I BOOTED, I GOT THE UBUNTU SCREEN, NOT GRUB.

Here's what I'm doing to try to fix this:

Divide flash drive into 3 partitions, grub on first, ubuntu on second, Kubuntu on third.  I'll do that and post if that problem is resolved, but even if it is I need to edit my GRUB menu still.  Please help people.  Thanks

---

### Post by reevine on 2009-05-20
ok boot into you flash drive and go ahead and boot into ubunutu.

now a small explenation as to why it's booting into your hard drive instead:

Each Ubuntu operating system is idetified by a UUID. this a specific identity code that points to a certain system. Root, which is different that UUID, is a specific way to point at a hard drive and partition.

what you want is to replace the UUID in the menu.lst file in your GRUB installation. and to go to the listing of your Ubuntu partition and change the UUID number that is listed. 

here is and example of what your entry should look like:

```

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8cfd73a3-5d46-41d0-beff-de66a0513019
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8cfd73a3-5d46-41d0-beff-de66a0513019 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

```

as you can see there are actually two places that you will have to replace the UUID for the Flash drive installation.

go to terminal and type (each line is a new entry):
```

sudo grub
find /boot/grub/stage1

```

you should have three partitions listed. im guessing it has shown the following:

```

grub> find /boot/grub/stage1
 (hd0,0)
 (hd1,0)
 (hd1,1)

```

if you only have one Ubuntu installation on your computer.

then type:
```

geometry (hd1)

```

check to make sure that its your flash drive. it should have:
```

drive 0x80: C/H/S = 30401/255/63, The number of sectors = 488397168, "/dev/sdb"
 Partition num: 2,  Filesystem type is fat, partition type 0xc
 Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
 Partition num: 5,  Filesystem type unknown, partition type 0x82

```

or something similar. check what drive it is. so it should be "/dev/sdb"

then type (each line is a new entry):
```

quit
blkid

```

look for /dev/sdb2
make sure it says TYPE="ext3"
then copy the UUID number (without quotations)

type in terminal (USB stands for the name of the flash drive. Please replace it with the name of your flash drive partition):

```

gksudo gedit /media/USB/boot/grub/menu.lst

```

this will open the menu.lst file so you can actually edit it.

then change the two UUID entries. Don't delete anything else.

then press save. and exit out of the menu.lst file.

go to the terminal and type exit

change the look of your ubuntu look before you reboot. so that it doesn't look like the default setup.

reboot and you should be able to boot into your Ubuntu on your flash drive.

---

### Post by reevine on 2009-05-20
ooops didnt see your update. that will change things. let me know all of your updated information.

---

### Post by papasmurf6768 on 2009-05-21
Thanks so much for replying!  Alright here's what I've got by myself:

I split it into two 1GB partitions, installed Ubuntu on the first, and Kubuntu on the second.  I then booted into the flash drive and I got the Kubuntu screen, so I booted back into my computer HD and installed GRUB to the Kubuntu partition, and now when I boot from the flash drive, I get the GRUB screen, so I'm back to my original situation of I need the correct info to put in the menu.lst.  I'll show you what I mean:


title        Ubuntu 9.04
XXXXXXXXXXXXXX

title            Kubuntu 9.04
XXXXXXXXXXXXXX


This is basically my menu.lst on my flash drive.  The X's represent what I need.  I need what to type to be able to boot from the Ubuntu sdb2 partition on my flash drive and my Kubuntu sdb3 partition on my flash drive.  (sdb1 isn't there, I deleted it, but I don't think it matters...correct me if I'm wrong.)

Once again, please notify me if you need any info, and thank you for replying!

---

### Post by reevine on 2009-05-21
ok it would be best if you had three partitions. 
you only have to make the first partition 32MB and FAT32. 
this will make it a lot easier to access the menu.lst file. 

Kubuntu is different and it uses a different filing system so im not sure how to access the right files from Ubuntu. 
thats why im asking if you could make a small 32 MB partition at the beginning of the drive. 

if your willing to do that then i can help you get this fixed a lot quicker.
if not thats fine we will just have to use Ubuntu to store the grub files.

let me know what your willing to do or can do.

---

### Post by papasmurf6768 on 2009-05-22
I can easily make a new partition.  I'll get it as soon as I get back from school, and I'll tell you when I'm ready.  If I get you right, my flash drive should have 3 partitions, all FAT32?  One smallone on the beginning, and 2 larger ones behind it?  That it what I'm doing, and I'll post a screen shot so you can see if it's right.

---

### Post by papasmurf6768 on 2009-05-22
Here's what the partitions are.  I'm suppose to put GRUB on the first, Ubuntu on the second, and Kubuntu on the third, right?

---

### Post by papasmurf6768 on 2009-05-22
Alright were all ready.  I have my partitions set up, you can see them in the previous post.  I installed GRUB to sdb1, Ubuntu 9.04 to sdb2, and Kubuntu 9.04 to sdb3.  When I plug in the drive and boot the computer, I get my flash drive GRUB menu, so were all ready for the information.  Now I just need what to input.  Thnaks a lot for helping me.

---

### Post by reevine on 2009-05-22
ok dude perfect. so what is the directory of the GRUB files on the first partition?

---

### Post by papasmurf6768 on 2009-05-23
media/disk-1/boot/grub

I think it's disk-1, I'd have to check.

---

### Post by reevine on 2009-05-23
ok boot into Ubuntu from your computer and then plug in your flash drive.

we are going to install GRUB on your flash drive itself. right now all you have are the files. go to terminal and type (each line is a new entry):
```

sudo grub
find /boot/grub/stage1

```

you should have three partitions listed. im guessing it has shown the following:

```

grub> find /boot/grub/stage1
 (hd0,0)
 (hd1,0)
 (hd1,1)

```

 if you get more than this let me know.

then type:
```

geometry (hd1)

```

check to make sure that its your flash drive. it should have:
```

drive 0x80: C/H/S = 30401/255/63, The number of sectors = 488397168, "/dev/sdb"
 Partition num: 2,  Filesystem type is fat, partition type 0xc
 Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
 Partition num: 5,  Filesystem type unknown, partition type 0x82

```

or something similar. check what drive it is. so it should be "/dev/sdb". there should be a couple more partitions because you have Kubuntu installed also. if this is the right one type:

```

root (hd1,0)

```

```

setup (hd1)

```

then exit and reboot.

let me know if it boots into your flash drive.

---

### Post by papasmurf6768 on 2009-05-24
Yes I've already done this.  When I boot my computer with it plugged in, I get my flash drive GRUB menu.  So we're ready to go.

---

### Post by papasmurf6768 on 2009-05-25
But once again I still need the correct info to put in the GRUB menu.

---

### Post by reevine on 2009-05-26
sorry about to delayed reply. i was gone for the weekend.

ok go to terminal and follow these instructions:

1. type:
```

blkid

```
(this will list bootable systems.)

2. If your booting off of your computer installation there should be and "/dev/sdb" listed with multiple partitions. your looking for the ubuntu one. it shoudl be the first listed entry. you are looking for:
```

/dev/sda1 uuid="fe7bf845-7ce9-4733-b6de-f70f2b62076d" type="ext3"

```
or something similar. if your not sure copy the results and paste the results.

3. copy the uuid number without the quotes.

4. then type in the terminal (replace "disk-1" with the name of your flash drive):
```

gksudo gedit /media/disk-1/boot/grub/menu.lst

```

5. when your menu.lst file opens got to the operation listings at the bottom. look for:
```

title    Ubuntu, kernel 2.6.20-15-generic
uuid     fe7bf845-7ce9-4733-b6de-f70f2b62076d
kernel   /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd   /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title    Ubuntu, kernel 2.6.20-15-generic (recovery mode)
uuid     fe7bf845-7ce9-4733-b6de-f70f2b62076d
kernel  /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro single
initrd  /boot/initrd.img-2.6.20-15-generic

title        
Ubuntu, memtest86+
uuid     fe7bf845-7ce9-4733-b6de-f70f2b62076d
kernel        /boot/memtest86+.bin
quiet

```

6. replace all of the uuid numbers for ubuntu with the number that you copied earlier. anywher it says uuid. in the kernel listings there are uuid numbers, replace those too.

7. then for your Kubuntu listing put:
```

title        Kubuntu
root        (hd0,2)
savedefault
makeactive
chainloader    +1

```

save the file and exit then reboot and you should be able to boot into ubuntu and kubuntu. let me know if you run into any problems.

---

### Post by papasmurf6768 on 2009-05-27
Alright we're half way there!  Kubuntu is up and running.  I'm having some trouble getting to boot from the Ubuntu partition of my flash drive.  I want to let you know that my UUID for partition sdb2, my Ubuntu partition, is weird.  When I enter "blkid", it says:

/dev/sda1: UUID="c4492f01-f775-4b08-b594-3701f4459edf" TYPE="ext3" 
/dev/sda2: UUID="09CA02F62B4925F5" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="719a5be9-d489-4d48-98ca-cb691333b88f" 
/dev/sdb1: UUID="F195-7977" TYPE="vfat" 
/dev/sdb2: UUID="F2E6-FA2A" TYPE="vfat" 
/dev/sdb3: UUID="F44B-A93C" TYPE="vfat" 

sdb UUID's aren't as long.  If I enter the sda UUID, won't it boot from the hard drive?  I don't know, I'll do it right now and see.  Thanks for all your help!

---

### Post by Yannick Le Saint kyncani on 2009-05-27
That may be beside the point, but why do you have two separate installations, one for ubuntu and the other for kubuntu ?

You do know that you can install both desktops on one installation, right ?  (install both ubuntu-desktop and kubuntu-desktop packages)

You can then select your desktop when you login ( a "session" or "select session" button in the login screen ).

---

### Post by papasmurf6768 on 2009-05-27
I don't think you get it.  I have two installations on my flash drive.  I want to be able to use GRUB to boot from both Ubuntu and Kubuntu partitions.  And here's what I'm getting in GRUB when I'm booting to Ubuntu:

"Error 15: File Not Found"

What does this mean any how can I fix it?

---

### Post by reevine on 2009-05-27
> **papasmurf6768 said:**
> I don't think you get it.  I have two installations on my flash drive.  I want to be able to use GRUB to boot from both Ubuntu and Kubuntu partitions.  And here's what I'm getting in GRUB when I'm booting to Ubuntu:

"Error 15: File Not Found"

What does this mean any how can I fix it?
ok simply change your ubuntu grub listings to look like Kubuntu but change the title to ubuntu and change the root to (hd0,1). this will be temerary. Im not sure why your UUID are funky. ill look into it and see if i can find out whats happening.

---

### Post by reevine on 2009-05-27
> **Yannick Le Saint kyncani said:**
> That may be beside the point, but why do you have two separate installations, one for ubuntu and the other for kubuntu ?

You do know that you can install both desktops on one installation, right ?  (install both ubuntu-desktop and kubuntu-desktop packages)

You can then select your desktop when you login ( a "session" or "select session" button in the login screen ).
i have heard of this but was not sure how to do it. i would like to know how.

---

### Post by papasmurf6768 on 2009-05-28
Since you've helped me I'll help you.  To install KDE, or the Kubuntu desktop, open a terminal and type:

sudo apt-get install kubuntu-desktop

When that's all done you'll be able to choose the session you want to use when you log in.  It takes a a good 750 MB though, so you might not have a lot of space left anfter installing.

---

### Post by papasmurf6768 on 2009-05-31
SOLVED!!!!!

THANK YOU SO MUCH EVERYONE!.  I just typed the things that reevine told me to and bam.  We're up and running.  Thanks.

---

### Post by reevine on 2009-06-02
im glad it works now!

---

