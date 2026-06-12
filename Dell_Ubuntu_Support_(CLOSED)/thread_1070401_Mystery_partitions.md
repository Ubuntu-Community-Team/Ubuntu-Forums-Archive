---
title: "Mystery partitions"
date: 2009-02-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dkaddict on 2009-02-15
I was recently given an Ubuntu pre loaded Dell Inspiron 1525 notebook. I did a fresh install as soon as I got the machine because I like to have a separate /home partition. When I loaded a Gutsy live cd and ran Gparted, there were 2 mystery partitions. One was a small 'fat16' partition, the other being a 5 GiB fat32 partition. I had to get rid of one of those partitions to create a separate /home partition, but I could only remove the small 'fat16' one and had to grow the fat-32 part into it to clean things up. Now I want to get rid of the 5 GiB fat-32 partition so I can dual boot. As it stands, I have 4 active partitions on the drive so I can't make room for a dual boot. I think that these partitions were put there by Dell instead of shipping a live DVD with the notebook? The partition I want to remove is mounted in /media/sda2 and looks very much like a live DVD. I think that the fat-16 partition I removed was the Dell re-installer for Ubuntu? Will I be ok to delete the fat-32 partition? I have a working Ubuntu Gutsy live cd so this partition, with what looks like a live DVD on it, is just wasting 5 GiB of my hard drive.

Any help or pointers in the right direction will be appreciated. I want to have an XP partition for playing a game or two and I just don't get on with WINE so... 

Cheers

PS-I just tried my live cd again. In Gparted on the live cd, because the partition is mounted in /media I can't do anything with it, it is locked. I just tried Gparted when my system was booted from my HD and it allowed me to unmount the partition and thus I can format it like that. I can't see how it will damage my system if I delete it and reassign it like that but I am not 100% sure? Will I be cool doing that?

---

### Post by ugm6hr on 2009-02-15
Likely scenario:

Small fat16 partition was the Dell Diagnostics partition
Larger fat32 is the Dell Recovery partition

Neither is *necessary*, but I would personally have kept the Diagnostics partition.

---

### Post by uidb4056 on 2009-02-15
As far as you have enough disk space may be better don't delete the partitions shipped by Dell, you can have more than 4 partitions creating one extended partition instead of primary partition (4 primary partitions allowed as a maximum) but you can have 3 primary partitions and 1 extended then you can create inside the extended partition as many logical partitions as you want if you have enough unallocated disk space.

---

### Post by dkaddict on 2009-02-15
Many thanks for getting back to me on this. I deleted the 'diagnostics' partition (it was ~93MiB), like an idiot, without looking into it when I first got the computer. I am pretty confident in being able to recover my system without the Dell diagnostic though. I am going to look for it on the Dell site and will try making an extended partition for it, or something like that, just in case. Would I be wise in doing so?

The /media/sda2 partition is definitely an Ubuntu DVD. I can unmount it ok so I will do that and delete it through GParted on a HD boot, then do the rest through the live CD while nothing is mounted. I like to have a spare partition for data I want to keep, and keep locked, or for a dual boot scenario.

Now I have to find a way of transferring the data from my old notebook onto this one. Both have built in wireless, so I can't see it being an issue. I haven't got a clue as to how to set up a home, wireless network, so it will be worth learning, and fun.

Thanks again for the advice.

---

### Post by caljohnsmith on 2009-02-15
If you would like to create more partitions on that HDD even though you now have the max four primary partition limit, it is possible to convert one or more of your primary partitions into logical partitions inside an extended partition, and then in the extended partition you can create about as many extra logical partitions as you want. If you would like help doing something like that, it would first help a lot to get a clearer picture of your setup and what is on your partitions, so how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by gbrainin on 2009-02-15
FYI, the default partitioning for a Dell that comes with Ubuntu is described here: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Default_Partitions]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Default_Partitions").  The utilities are primarily hardware testing, which can be handy if you think your hardware may be faulty.  The reinstall partition will _repartition and wipe_ your entire hard drive and return it to factory default (including restoring the utility partition, I believe).  The other partitions are for Linux.

---

### Post by ugm6hr on 2009-02-15
Given it's now gone, I wouldn't bother with the Dell partitions.

The only scenarios they are useful:
1. Computer under warranty and you need to call Dell support
2. The CD drive / USB ports are broken so you can't boot any form of system check CD to check hardware

Both USB and CD drive failing at the same time would be unusual...

---

### Post by BigSilly on 2009-02-15
> **ugm6hr said:**
> Given it's now gone, I wouldn't bother with the Dell partitions.

The only scenarios they are useful:
1. Computer under warranty and you need to call Dell support...

Surely even then it's only useful to them if you are running Windows, no? We only use Ubuntu here. I'm buying a Dell 530 soon, and have seen this setup on my missus' Inspiron 1525 too. That came with 7.10 Gutsy installed, and when time came to upgrade to Intrepid for her, I just let the Ubuntu disc wipe the hard drive clean and take the whole thing. I was going to do the same with my own Dell. Would you recommend against it then?

Thanks.

---

### Post by ugm6hr on 2009-02-15
> **BigSilly said:**
> Surely even then it's only useful to them if you are running Windows, no? 

I don't understand why a Diagnostic partition would only be useful for Windows.  Hardware problems, and the need to phone for support from Dell, are largely independent of OS.

Again, I would keep the restore partition until the warranty expires (or create a restore DVD), simply because the first thing Dell will do if there is a problem is tell you to restore the OS to rule out a software issue.  If you have wiped that partition, you are potentially requiring a return to OEM, which may or may not be necessary (depending on your own ability to diagnose hardware vs software problems).

Your choice though.

---

### Post by BigSilly on 2009-02-15
> **ugm6hr said:**
> I don't understand why a Diagnostic partition would only be useful for Windows.  Hardware problems, and the need to phone for support from Dell, are largely independent of OS.

Again, I would keep the restore partition until the warranty expires (or create a restore DVD), simply because the first thing Dell will do if there is a problem is tell you to restore the OS to rule out a software issue.  If you have wiped that partition, you are potentially requiring a return to OEM, which may or may not be necessary (depending on your own ability to diagnose hardware vs software problems).

Your choice though.

I was only asking because I wasn't sure what it was! I didn't know at all, hence my question. I just imagined that it would be a Windows related diagnostic partition, and useless to Linux users. Sorry for any confusion.

If you reckon it's worth keeping around, then for sure I'll keep it around. I've never bought a PC from Dell before, and am unaware of the etiquette and procedure involved. Thanks for letting me know, it's much appreciated. :)

---

### Post by dkaddict on 2009-02-23
For what it is worth: I now have the 1525 with my normal partition set up, the way I had it on my old notebook. I am happy with the knowledge that I have a live CD in case anything goes wrong (which is always down to me, not Ubuntu). I am definitely going to look into the logical/extended partition set up, however, because I may need space for a Kubuntu install(I don't get on with KDE files all over the place) or perhaps another distro? Either way it seems like handy knowledge to have on board. This Inspiron is a good machine and runs everything faultlessly, well so far anyway.
Many thanks.

PS-caljohnsmith, I will have a go at finding out how to do the partitions on my own (best way to learn) but may have to post that output you mentioned, so I will be in touch if needs be. Thanks again.

---

### Post by Rallg on 2009-02-23
A small primary FAT partition can be useful, particularly for those of us (mini 9 users) who have no CD-ROM drive. I just updated my BIOS using a DOS program from Dell. To boot DOS, I used a USB formatted as a phony bootable 1.44 floppy (which cannot store other files, and is regarded as drive A), and put the BIOS updater on a primary DOS partition, which is interpreted as drive C.

---

