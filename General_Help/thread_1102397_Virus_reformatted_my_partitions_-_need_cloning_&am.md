---
title: "Virus reformatted my partitions - need cloning &amp; recovery software recommendations"
date: 2009-03-21
forum: General Help
---

### Post by callie510 on 2009-03-21
Oh please, I hope y'all can help me. I'm a fourth year college student with a 100 page thesis due in two weeks -- and a Windows virus just reformatted most of my partitions. Including my Linux /home partition, where all my photos and music and documents live! Luckily I keep all my academic work on my university network drive. My thesis is safe. But as for the rest of my precious files - my 20 gigs of photos, a lifetime of writing, a big music library - it's all gone right now.

Please help!! 

I think the details don't matter much. Right now I am booted onto an Ubuntu Live CD, and here are the troubling signs that lead me to believe the drive is right now unsalvagable:
[LIST]
[*] "sudo fdisk -l" shows two "NTFS volume set" partitions where my Linux ext3 partitions used to be. (and what's up with that? Usually my Windows partitions are listed as "HPFS/NTFS") 
[*] The sizes appear to be completely wrong, too. I think two of the affected partitions were merged.
[*] Gnome Partition Editor doesn't see any partitions at all, and thinks my drive is 160GB unformatted.
[/LIST]

This leads me to believe that the drive is currently too damaged to be recovered at all and needs to be wiped and repartitioned. Please correct me if I'm wrong, but I think it's unsalvagable.

So I'm looking to do this:
1) Clone the whole drive onto an external
2) Run data recovery software on the clone
3) Wipe my internal drive, re-partition, reinstall, and copy back as much data as I can recover.

Can someone please recommend software that will do this? Cloning software that works on corrupted or damaged drives? Data recovery software that will read ext3? I have used Norton Ghost in the past, but that was before I saw the light and switched to Linux. I don't believe Ghost will do the trick here, but correct me if I'm wrong. 

I have no idea what software to use, and I'd rather get recommendations from intelligent Linux users rather than just googling. Thanks for any help! Your replies will reduce the stress of this college student who was *already* about to jump off a building *before* a virus reformatted her computer. :)

edit: I have learned my lesson about backups and have already purchased an external drive so this never, ever, ever happens again. And I'm done with windows! Forever! This never would have happened to me if I had been using Linux last night! Ugh.....

---

### Post by S.A.A on 2009-03-21
I highly recommend testdisk (available for linux & windows, grap it from here [http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")).
I had similiar problem to yours, and that program did all of what i need. It's simple, open-source, small and very easy to use.

---

### Post by Jimmey on 2009-03-21
Yeah, you can use testdisk to try and find/re-instate lost partitions, or you can use photorec to recover files.

How do you know that it was a virus that caused it?

---

### Post by hikaricore on 2009-03-21
> **callie510 said:**
> Your replies will reduce the stress of this college student who was *already* about to jump off a building *before* a virus reformatted her computer. :)

Hope you're joking about jumping off a building...
I personally take such statements very very seriously.

If you need anyone to talk to outside of your help request feel free to PM me.

---

### Post by mini_g on 2009-03-21
The last I checked, Ghost can copy the existing sectors to a cloned file.  I can't remember the proper options term for it though.

---

### Post by S.A.A on 2009-03-21
> **callie510 said:**
> I have learned my lesson about backups and have already purchased an external drive so this never, ever, ever happens again. And I'm done with windows! Forever! This never would have happened to me if I had been using Linux last night! Ugh.....
Just hope the lesson won't be so hard, but that doesn't mean these problems are far away from Linux, It just happens wither from human or nonhuman mistakes.

---

### Post by rhcm123 on 2009-03-21
I highly reccomend r-studio. It's one of the reasons i keep windows around. Read the review here: [at this link.]("http://data-recovery-software-review.toptenreviews.com/r-studio-review.html")


Although it may be ugly and makes assumptions that you know what you are doing, it never misses a file and even works with ext2 and ext3 file systems! I use it when i fix my friends computers (they think i have a clean room in the basement - i just fix the NTFS file system with a few commands on linux then hand it back to them - $50 )

---

### Post by callie510 on 2009-03-21
Thank you all so much for your incredibly fast help! I will try the programs listed - testdisk and/or photorec, or r studio, although I am very poor so open-source is definitely preferable. I never would have found that stuff just googling. I am a relatively new Ubuntu user, and I just don't know the tools available to me.

These forums are so fast! Thank you all!!

---

### Post by callie510 on 2009-03-21
How do I know it was a virus? Well, my university kicked me off the network due to "malicious activity" minutes before my partitions disappeared.

I wasn't stressed out at all at this point - after all, my Linux partitions are totally separate from Windows!! - until I attempted to boot into Linux and the boot failed miserably. fstab had an entry referring to a partition that didn't exist. What? I booted onto the Linux Live CD and checked "fdisk -l." My /home partition was listed not as "ext3", but as "NTFS Volume Set." WHAT! OH NO! This is where I started to flip out.

However, at this point, it still might not have been the virus. I had never been able to get my ext3 partitions to mount correctly in Windows. Every time I clicked them in My Computer, Windows prompted me to format. Maybe I clicked yes? By accident? Unlikely but possible? However, probably about 30 minutes later after trying to fix some stuff, I went back to the Linux Live CD and checked "fdisk -l" again. This time, TWO partitions were missing. /home and root. I had to rub my eyes because I thought I was dreaming. 

I definitely got a virus this morning, and I basically watched as two of my partitions disappeared. This is why I believe it to be the work of the virus. I could be wrong..... but that's what happened!

---

### Post by rhcm123 on 2009-03-21
> **callie510 said:**
> Thank you all so much for your incredibly fast help! I will try the programs listed. I never would have found that stuff just googling. I am a relatively new Ubuntu user, and I just don't know the tools available to me.

These forums are so fast! Thank you all!!

just so you know r-studio is pricey, but it's worth the money.

---

### Post by callie510 on 2009-03-27
Thanks guys - y'all saved my life. I burned a copy of Ultimate Boot CD and loaded up testdisk, and within minutes it had identified my partitions and fixed them all right back the way they were supposed to be.

Now ... I have one more question. I am replacing my hard drive - in this fiasco of formatting I decided to get a nice big new one - and I would like to image my ext3 partitions. I've used Ghost on windows but I don't think that will work with ext3 (???). I've also seen a lot of tools which will image, but won't work with a USB hard drive.

What is the best program to use to image my partitions to an external USB hard drive?

Thanks!

edit: Some way to image from within Windows or Linux would be very nice. The tools I've seen for imaging from a boot disk don't support USB hard drives - although I could be wrong.

---

### Post by mal_conductor on 2009-03-29
I had a similar problem.  TestDisk and Photorec are good.

I made these notes to help people in this situation.

[http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871)

---

### Post by rhcm123 on 2009-04-02
> **callie510 said:**
> 
edit: Some way to image from within Windows or Linux would be very nice. The tools I've seen for imaging from a boot disk don't support USB hard drives - although I could be wrong.

I also think there is an NTFS recovery tool called scrounge-ntfs kept in the repositories. apt-get it and try it out, i've never used it myself

---

### Post by JKyleOKC on 2009-04-02
> **callie510 said:**
> What is the best program to use to image my partitions to an external USB hard drive?

Do a Google search for "Acronis True Image" and look especially for references to a free download of Version 7 or thereabouts. While you would have to use Windows to run the program initially, it includes the creation of a standalone boot disk that actually boots into Linux to create the image, so you could create such a disk, close the program, get out of Windows, and use TI to do the imaging.

I've used it and was so happy with it that I bought a later version. It does have a few quirks; one is that it sometimes decides to do a sector-by-sector copy of the disk rather than a compressed image, which can take literally hours on a disk as small as 30 GB when writing to an external USB drive. However, for free it's worth trying...

---

