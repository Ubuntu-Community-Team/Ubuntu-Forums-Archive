---
title: "Dula Boot installation"
date: 2009-03-14
forum: General Help
---

### Post by krelian99 on 2009-03-14
Hi everybody
I'm new here:P

need some help:
I desperately need to use Linux for a project I'm doing at my university.
Now I dont have a PC yet but my friend allowed me to "mess" with his, provided I dont **ck up his Windows Xp install.

I did a lot of research but didn't find anything that best suits my needs.
I'd like to (actually HAVE TO)  
keep WinXP as a primary OS at boot, I obviously don't care either about file sharing and such.
Basically I need to install ubuntu in the least intrusive way as possible
 
oh btw
I've already resized the WinXP partition and now have 10Gb of unallocated space

I hope my post make even just a "bit" of sense
thanks

---

### Post by krelian99 on 2009-03-14
Apologies if I opened this discussion in the wrong section
I just now realized there's a "Absolute Beginner Talk" section

if any mod can move this thread (and fix the typo in the title) it'd be much appreciated as I don't want to open a new thread

---

### Post by mikewhatever on 2009-03-14
You can either install to that 10 GB unallocated space, or inside the Windows partition, provided there is enough space. Is there a problem of any kind?

---

### Post by krelian99 on 2009-03-14
thanks A LOT for the reply

the reason I'm confused is there are so many guides all around and all differ slightly or substantially.
I'm a noob and and I still don7t get all the talk about concepts like /boot partition or Linux swap 

I'll certainly install it in the unallocated space and as I said I'd like to have WinXP as master boot

shall I format the unallocated space as secondary partition?

---

### Post by mikewhatever on 2009-03-14
Well, there are several ways to install and many ways to partition. If there is an option similar to 'Guided - use the largest continuous free space', choose that, and all the partitioning will be done for you. If not, you'd have to go with the manual partitioning option. I don't know what a secondary partition is, but if you mean primary vs logical, then it makes no difference.

---

### Post by martrn on 2009-03-14
Make sure you are partitioning the hard drive properly, and do NOT delete format partition or otherwise wipe the windowze partition.  

If you have allocated unallocated space (or unallocated space) of 10GB  as secondary partition if might be a good idea to format the partition at some point or you will not be able to use it.

You can format the file system as EXT3 or any linux file system.

Its good to have some space as a linux swap file as this improves performance under ubuntu by allowing extra memory for pre-fetching applications and is built in to the linux kernel.

If you don't want any swap space you could use all of the 10GB as your ubuntu file system, if you do want swap space, split the 10GB into a small swap space and then the remainder as EXT3 of whatever file system you choose.

---

### Post by sailthesea on 2009-03-14
I know its not a popular choice amongst many users but I always like to try an initial test on any system using Wubi, this installs Ubuntu within windows and gives you a chance to check it out before you do anything major and permanent It might also reassure your friend that your not going to *%$* up his machine

---

### Post by krelian99 on 2009-03-14
> **mikewhatever said:**
> I don't know what a secondary partition is

eh, just me being silly

thanks a lot everybody, I already love this community.
I can't wait to make myself a new build next month and use ubuntu as my primary OS, I'm really tired of Windows

I guess I'll just pop in the Live CD and follow instructions.
For some reason I thought it couldn't format and I had to do that through WinXP's management

as I said my main concern was that I needed to do "something" that let WinXP being the main OS
one of the guides I checked is this:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=4]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=4")
and that GRUB boot menu got me confused

---

### Post by mikewhatever on 2009-03-14
If you mean that you want XP boot by default instead of Ubuntu, that's easily achieved. When done installing, post GRUB's menu here, and someone will tell you what to change.

Edit: If you think about it, when dual booting, nether OS is main or secondary. Both are on separate partitions, can read from and write to each others partitions if appropriate firmware is installed, and lastly, one can choose what to boot from the menu. I guess that makes them independent.

> **sailthesea said:**
> I know its not a popular choice amongst many users but I always like to try an initial test on any system using Wubi, this installs Ubuntu within windows and gives you a chance to check it out before you do anything major and permanent It might also reassure your friend that your not going to *%$* up his machine

Why is wubi unpopular? Under the OP's circumstances, I'd say it is a better choice.

---

### Post by martrn on 2009-03-14
> **krelian99 said:**
> ..I guess I'll just pop in the Live CD and follow instructions. For some reason I thought it couldn't format and I had to do that through WinXP's management..and that GRUB boot menu got me confused.

Grub is a boot-manager installed to the MBR and works quiet well.  If its not your computer or you don't want to write anything to the MBR see :

[http://en.opensuse.org/SDB:Booting_Linux_with_the_Windows_NT/2000/XP_Boot_Manager]("http://en.opensuse.org/SDB:Booting_Linux_with_the_Windows_NT/2000/XP_Boot_Manager")

If you can install Grub to the MBR then just install grub and boot into ubuntu and get it to boot windowze straight away.

[https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto")

---

### Post by krelian99 on 2009-03-15
all set:KS
it wasn't that hard frankly, I worried for nothing

I added a 250MB swap partition at the end as well

the only awkward moment is when it asked for mount point as I have no idea what that is
I chose the first option **/** and all went smooth

> **martrn said:**
> 
[https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto")

that helped me a lot, thanks
I set WinXP as default no prob in the automagic kernel list

now it's time to get serious. I'll have to deal with SIPp, openssl and c++ :shock:

thanks again everybody

---

### Post by munishvit on 2009-03-15
Sorry to mix-up my problem with this thread, but I too have problem with dual-boot and I want to install Windows XP on non-first primary partition. Please Check
[http://ubuntuforums.org/showthread.php?t=1095893](http://ubuntuforums.org/showthread.php?t=1095893)
aaanny help would be great. Thanks :D

---

