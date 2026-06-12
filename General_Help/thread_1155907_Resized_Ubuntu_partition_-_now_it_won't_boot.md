---
title: "Resized Ubuntu partition - now it won't boot"
date: 2009-05-11
forum: General Help
---

### Post by macdonaldjnew on 2009-05-11
Hi there,

I'm hoping someone might be able to help me out with a Gparted/Ubuntu-Vista dual boot problem. I've read just about all the partition-related threads on here and am still trying to figure out the best way to fix my machine.  Here are the details:

I am running a Dell XPS M1530, 250Gb SATA drive, 4Gb RAM. I had the drive split 110Gb Vista, 110Gb Ubuntu and the rest was the various mediadirect and recovery partitions that the laptop came shipped with. 

I have been using Ubuntu for about a year now and have become a total convert and so decided to shrink my Vista partition by 50Gb using Gparted via a Puppy linux livecd, then expand my Ubuntu partition by sliding it to the left (in Gparted) and increasing it to use the rest of the space on the disk. 

Well shrinking Vista made my machine unbootable. (A quick note here - In the past I had reinstalled the Windows bootloader as i preferred the look of it over Grub). After the Dell BIOS screen loaded there was nothing but a blinking cursor, no error message, nothing. Freak! After a few hours of troubleshooting I gave up, formatted the newly shrunk partition and reinstalled vista, and used EasyBCD to add the Ubuntu entry to the bootloader. That all worked fine and everything was good and happy, until....

I turned my attention to the Ubuntu partition. I created a Gparted live cd and booted into that and then moved and expanded the Ubuntu partition from 110 > 160 GB. It took about three hours, but I woke up this morning to find it had completed successfully.  I restarted, the Windows bootloader came up, I selected Ubuntu from the list and an error message came up (I think from Grub) saying "Cannot boot from system disk, please insert disc..." or something along those lines. 

From what I've read so far, I suspect that the partition is there but Grub just needs to be told where to find it, although I'm not sure. Also what info should I be looking at to try and solve this? I have the Ubuntu, Puppy and Gparted LiveCDs, and I know that the experts on here will need to know more about my partition table, so would appreciate if you could tell me what info you need so I can post it up here and may be you could help me?  I am very reluctant to wipe my ubuntu partition and start again as I invested quite a bit of time configuring it. Thankfully though I do have the lion's share of my important data backed up. Sorry for the long post!

---

### Post by skymera on 2009-05-11
Try reinstalling GRUB from the Ubuntu LiveCD

ok, once your in the CD open the terminal

```
grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0) 
```

That's basically it. The numbers will change accordingly to your system. I used 0's as they're what i use.

That should find your Ubuntu and Vista, *** them both to the grub menu. Hey presto, it should work :)

@ When you resized Ubuntu ,was it EXT4 Jaunty?

---

### Post by macdonaldjnew on 2009-05-11
Wow, thanks for the speedy response! Regarding your question about the filesystem, I had upgraded to Jaunty using Ubuntu Update Manager, so I'm not sure whether it would have changed it to EXT4, or just left it how it was. Unfortunately I am at work now so I don't have the machine in front of me to check it. Would that affect the size of the blocks moved in Gparted or something?

I will try to reinstate Grub when I get home tonight and report back. Thank you very much for the help!

---

### Post by skymera on 2009-05-11
EXT4 isn't the default filesystem for Ubuntu.

I'm just curious. as far as i'm aware Puppy doesn't support EXT4, so resizing could lead to breakage is why i asked :)

I'll keep an eye on this thread to see your reply later.

---

### Post by macdonaldjnew on 2009-05-11
Ah ok, although I didn't use Puppy to resize the Ubuntu partition. I just used that for moving Vista. Sorry I should really clarify the steps that I took a little better:

1. Shrank Vista volume using Vista's own disk manager
2. There was about 5GB free space before the Vista partition that I had created from shrinking the recovery partition, so I...
2. Moved the Vista partition over to use up this 5GB, using Gparted on Puppy live cd
3. Vista did not work after that so reinstalled it on the same partition
4. Used Gparted LiveCD to move Ubuntu partition back to the newly freed-up space left by shrinking the Vista partition, and increased it to take up the rest of the space on the disk.
5. Now Vista will boot ok, but Ubuntu will not.

Anyway I will follow your instructions tonight and let you know, thanks!

---

### Post by macdonaldjnew on 2009-05-11
Ok I am back homw, booted into LiveCD and went straight into terminal > grub and I get an error message 15: file not found message when i ask it to find stage1. Any ideas? I tried mounting the Ubuntu partition and it looks like all the data is there. Gparted shows all the partitions in place. Tried that find command in grub again after I mounted the partition and got the same file not found response.

---

### Post by macdonaldjnew on 2009-05-11
Ok silly me forgot to run grub as root! So running find returned the following and then i typed in the rest as you can see below:

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

I will now try to reboot and report back.

---

### Post by macdonaldjnew on 2009-05-11
It worked like a charm, YAY! Thanks so much for your help, it is MUCH appreciated! Loving the Ubuntu forums :)

---

### Post by Roasted on 2009-05-11
> **macdonaldjnew said:**
> It worked like a charm, YAY! Thanks so much for your help, it is MUCH appreciated! Loving the Ubuntu forums :)

Glad to see you got your problem fixed and the forums were able to help you.

There's a great group of people here who are dedicated to helping users out with issues. In my 4 years of Ubuntu, I've had some answeres go unanswered, and some that were answered within 2 minutes of me posting. More times than not, my problems were fixed here on the forums.

Keep on Ubuntu-ing! :guitar:

---

### Post by fizzybrain on 2009-06-16
(I'm appending to this thread in case anyone else has similar problems - sorry it's so long, but I'm trying to be precise))

I have similar problems!
I had/have a triple boot system, as follows:

 ------------------------
|sda1 XP system (NTFS) (with GRUB4DOS for booting Kubuntu 8.04)
 >------------------------
|sda2 old linux boot (now unused)
|sda3 /============\ (extended)
   >------------------------
  |sda5 DATA (NTFS)
   >------------------------
  |sda6 LINUX HOME
   >------------------------
  |sda7 LINUX (Kubuntu 8.04) - older fallback (little space, to be expanded)
   >------------------------ ( V  to be resized that way)
  |sda8 LINUX SWAP (small, to be expanded to allow hibernation)
   >------------------------ ( VV to be resized that way)
  |
  |
B |sda9 LINUX (Kubuntu 8.10) - primary OS (much space, to be shrunk) BOOTABLE
  |
  |
   >------------------------
  |sda10 old FAT16 partition (for emergencies)
\========================/
(94MiB unallocated - diagnostic partition, I think)

sda was set bootable, and the GRUB menu there allowed me to jump to the XP bootloader on sda1, from which I could either boot XP or run GRUB4DOS to then boot sda7. Not elegant, but it worked (and I reckon it presented some immunity to cock-up).


I wanted to upgrade the kubuntu 8.04 on sda7, but leave kubuntu 8.10 on sda9 as that is a known-good(ish) system.
So, booting from sysrescue CD/gparted, I did the following:
1. resized sda9, shrinking by 2GB (moved the sda8/sda9 boundary only)
2. moved/resized the swap partition
3. resized sda7, increasing by 1.5GB (moved the sda7/sda8 boundary)
i.e:

...
 >------------------------
|sda7 LINUX (Kubuntu 8.04)
|
|
 >------------------------
|sda8 LINUX SWAP 
|
 >------------------------
|sda9 LINUX (Kubuntu 8.10) bootable
 ------------------------

Now sda9 will not boot, even though it is set bootable.
By setting sda1 bootable I can still get to sda7 (hurrah for backups!).

Booting from sysrescueCD I run
  grub
  grub> find /boot/grub/stage1
    (hd0,1)
    (hd0,6)
which I think corresponds to sda2 and sda7 - nothing about sda9

carrying on...:
grub> root (hd0,8 )
  Filesystem type is ext2fs, partition type 0x83
grub> setup (hd0)
  Checking if "/boot/grub/stage1" exists... no
  Checking if "/grub/stage2" exists... no
  Error 2: Bad file or directory type

My first thought was that the partition table entries had been re-ordered, but fdisk -l shows no such problem

Any ideas how I can make this sda9 bootable again?
Alternatively, how can I add it to the menu.lst on sda1 so I can boot it from GRUB4DOS? (though I tried this before with little success - "file not found" messages, IIRC)

Thoughts?

Share And Enjoy, folks

---

### Post by fizzybrain on 2009-06-17
Curious - I tried again from within the kubuntu 8.04 partition, and it found /boot/stage1 fine on (hd0,8 ), then root-ed and ran setup and it installed perfectly. It even preserved my menu.lst. hurrah.

---

