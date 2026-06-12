---
title: "easy dual-boot install with XP, but hard-disk partitions messed up"
date: 2005-12-24
forum: General Help
---

### Post by danrop on 2005-12-24
Hi all,

Last night I installed Ubuntu 5.10 to dual-boot with XP on my HP DV1000 Pavilion laptop without any apparent problems (I must say I was very impressed when the installation went without a hitch; a previous installation of SuSE had given me countless headaches.) 

Before installation, my 80 GB HD consisted of a 73.8 GB NTFS partition + 200 MB bootable (Linux-based, I think) partition that is used to "quick play" DVDs without having to boot up XP (this is standard in DV1000 laptops). I left the 200 MB partition untouched, and reconfigured my NTFS partition as follows:

1) Resized the 73.8 GB NTFS to 45 GB NTFS.
2) At the*end* of the free space now available I created a 2 GB FAT32 partition with a mount point /sharedfat32, with the idea of using this as a shared space between XP and Linux.
3) I let the partitioning utility deal with the rest of the available space; it partitioned it into the Linux filesystem partition + 1.4 GB swap space.

So far so good; the installation completed without a hitch, and Ubuntu is working fine. However now when I'm in XP -btw GRUB booter- I see (through the 'My Computer' utility) that I have a 45 GB C: drive and an unsized E: drive which XP claims is "Raw" when I right-click for properties (no sign of the FAT32 partition either). If I use Partition Magic to examine my HD now, it shows the whole HD to have a bad partition table, and doesn't even identify the NTFS partition. 

OK, so back to Ubuntu, if I run " sudo fdisk -l" in the terminal, I get the following:
************************************************
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5471    43945776    7  HPFS/NTFS
/dev/hda2            9704        9729      208845   88  Linux plaintext
/dev/hda3            9294        9703     3293325    f  W95 Ext'd (LBA)
/dev/hda4            5472        9293    30700215   83  Linux
/dev/hda5            9461        9703     1951897+   b  W95 FAT32
/dev/hda6            9294        9459     1333332   82  Linux swap / Solaris

Partition table entries are not in disk order
****************************************************

So what's going on here? How can fix it so the HD partitions are properly identified  under XP and Partition Magic? I also don't know where my FAT32 partition is supposed to be in Linux; it's not in /sharedfat32 at least.

Any and all help will be appreciated!

Cheers!

---

### Post by xmastree on 2005-12-24
[QUOTE=danrop]/dev/hda1   *           1        5471    43945776    7  HPFS/NTFS[/quote]That'll be your new 44GB Windows partition, no problem there.> /dev/hda2            9704        9729      208845   88  Linux plaintextThat'll be your 200MB DVD player thing
Between the end block of Windows and the start block of the DVD thing you have:
> /dev/hda4            5472        9293    30700215   83  Linuxand> /dev/hda3            9294        9703     3293325    f  W95 Ext'd (LBA)which contains> /dev/hda6            9294        9459     1333332   82  Linux swap / Solaris
/dev/hda5            9461        9703     1951897+   b  W95 FAT32
So something is a bit strange there. You said you made a 2GB partition at the end, but hda3 shows up as 3GB, with 2GB allocated to FAT32 as hda5. It seems to be sharing a partition with Linux swap.

Since Partition magic can't make out what's happening any more, I suggest you grab a copy of [the ultimate boot CD](http://www.ultimatebootcd.com/) and remove everything but the 44GB NTFS and the 200 linux DVD partitions.

Then, I would make a 2GB secondary partition, just above the Windows one, starting at 5472 and fill it with one virtual disk, to be formatted FAT32.

At this point I would probably boot Windows, to make sure it sees it.

Then, run the ubuntu installer again, to install in the free space.

---

### Post by danrop on 2005-12-24
Thanks a lot for your reply, xmastree. I'd figured that there was something funny going on with hda3... I think I'll proceed along the lines you suggested.
My knowledge of HDs is rather fuzzy, but I wonder if this has something to do with the fact that a hard disk can only have 4 primary partitions, so in my case where I want to divide my harddisk into 5 chunks (logically speaking), I need to have one partitions assigned as an 'extended' partition and subdivided into logical partitions (in my case the FAT32 and Linux swap). And since my present setup doesn't seem to be working properly, does this mean that there is something wrong in having logical partitions of two very different file-systems, i.e. FAT32 and Linux?

---

### Post by xmastree on 2005-12-24
You've got me thinking now, about the maximum 4 primary partitions thing.
NTFS on one, FAT32 shared, DVD player, that means that you can only have one more. I think that linux at least tries to put swap in its own partition even if the rest is all together.

Do you ever use that DVD player thing, it might be better to dump that.

And, (this is a personal preference, yours may well vary) I would have a much larger shared partition and smaller XP one. Music, photos, 2GB soon fills up. I would go 20/40/20

---

### Post by danrop on 2005-12-24
I think I'll try out the ultimate bootable CD you suggested first, and get rid of everything except NTFS and the DVD player (I'd rather keep it than get rid of it). 
However (assuming everything goes well upto this point) this time i'll use Partition Magic to configure my partitions before installing Ubuntu, and hope Ubuntu picks it up during installtion. 

Actually that's what I did when I previously installed SuSE on the same laptop; and although I'm not 100% sure, I believe my partition structure was pretty similar to what I attempted to do with Ubuntu now, only I did it through Paritition Magic, and everything worked fine with Windows and SuSE, HD-wise. (But then SuSE 9.3 gave me so many ACPI problems - it actually caused my CPU fan to burn out! - that I got rid of it, reformatted everything and reformatted/remerged all the partitions to NTFS).

I do have another question  though; will there be any potential problems with the Grub loader after I get rid of Ubuntu and reinstall it? Personally I'd feel more comfortable if I could restore the Master Boot Record (MBR) to XP's before I set out to reinstall Linux. I could do that from within SuSE, is there anything equivalent under Ubuntu?

Re the size of the shared partition, personally I don't think I need to swap that much between XP and Linux. My main reason for installing Linux was because we use Linux at my office in the Univ, and I often like to remotely login using ssh and work from home. But then again, I've only been using Linux for a month or so, and the more I use it, the more I like it! I do have an external 200 GB Maxtor HD though (mainly for the media stuff: audio, movies and the like) and I could repartition that and create some shared space there if need be.

---

