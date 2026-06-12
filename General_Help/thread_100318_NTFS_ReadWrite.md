---
title: "NTFS Read/Write?"
date: 2005-12-07
forum: General Help
---

### Post by apsalyers on 2005-12-07
Is it possible to mount a windows partition as read/write instead of read only?

---

### Post by SkillZero on 2005-12-07
i would like to know too..

---

### Post by Bachstelze on 2005-12-07
Yes. But bear in mind that if you write onto a NTFS partition from linux, the risks of losing the entire partition are pretty high.

---

### Post by frodon on 2005-12-07
No write support for NTFS in linux. The only project about write access is captive, you have to install it and of course you have some chance to lose some datas therefore i don't think it's a good idea.
If you want to use linux as your first OS use ext3 or reiserfs, if you want to use both windows and linux use FAT32 FS for your datas.

Good luck.

---

### Post by apsalyers on 2005-12-07
Write support for NTFS has been available in releases of SuSE, at least from 9.0+, which are my experience years with it.  Granted, until 10 OSS edition, SuSE has not been a completely free distro.

EDIT: Not really an urgent issue, as of now I use my USB key or my external HD formatted to Fat32 to carry out OS to OS transfers locally.

---

### Post by Bachstelze on 2005-12-07
And remember that you can ALSO install Win XP on FAT32.

---

### Post by soulestream on 2005-12-07
> Write support for NTFS has been available in releases of SuSE, at least from 9.0+, which are my experience years with it.

NTFS write support is built into the kernel. However, this is the caveat. You can change any file as long as you don't change its exact size. Therefor, writing to NTFS == bad.

soule

---

### Post by penvzila on 2005-12-09
I wonder is there a program that allows Windows to read/write ext3 volumes safely?

[]("http://uranus.it.swin.edu.au/%7Ejn/linux/explore2fs.htm")

---

### Post by mherring on 2005-12-09
IMHO, the way to do this is have a data dirve (or partition) formatted as FAT32---this can be used read/write by both Windows and Linux with no issues.  From each OS, set up pointers to the data drive.

Another advantage of this is you can install/reinstall your OS(s) with minimum risk to your data.

---

### Post by IdolizingStewie on 2005-12-09
[QUOTE=penvzila]I wonder is there a program that allows Windows to read/write ext3 volumes safely?

[]("http://uranus.it.swin.edu.au/%7Ejn/linux/explore2fs.htm")[/QUOTE]

You need to put text between the URL tags for the link to show up. I didn't realize you'd answered your question until I quoted it. [penvzila's link to Explore2fs.]("http://uranus.it.swin.edu.au/%7Ejn/linux/explore2fs.htm")

---

### Post by soulestream on 2005-12-09
there is also a secondary driver to allow linux to write to NTFS, if i remember correctly. Just dont know how stable it is. 

[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)

[http://sourceforge.net/projects/linux-ntfs/](http://sourceforge.net/projects/linux-ntfs/)


soule

---

### Post by Lux Perpetua on 2005-12-10
[QUOTE=HymnToLife]And remember that you can ALSO install Win XP on FAT32.[/QUOTE]Probably, but it isn't straightforward. The only time I installed Windows XP, the drive was actually formatted FAT32, and the Windows installer automatically reformatted it to NTFS without asking. (The change is not reversible.)

---

### Post by linkunderscore on 2005-12-10
[QUOTE=Lux Perpetua]Probably, but it isn't straightforward. The only time I installed Windows XP, the drive was actually formatted FAT32, and the Windows installer automatically reformatted it to NTFS without asking. (The change is not reversible.)[/QUOTE]

I was under the impression that XP could not be installed on FAT32. It needs NTFS. 
All installs of XP automatically convert FAT32 to NTFS (at least the partition where XP is installed to is converted). This has been my experience and what I have heard from friends.

---

### Post by bonzodog on 2005-12-10
AFAIK, as of SP2 the possibility of using FAT32 under XP as it's base filesystem was removed because of the limits placed by FAT32 on size of filesystems.

---

### Post by Thunk on 2005-12-10
[QUOTE=bonzodog]AFAIK, as of SP2 the possibility of using FAT32 under XP as it's base filesystem was removed because of the limits placed by FAT32 on size of filesystems.[/QUOTE]

But is it possible for XP to handle a secondary FAT32 partition (not the one it's installed on)?

---

### Post by cbudden on 2005-12-10
I have Windows XP installed on a Fat 32 partition, and it is fine.

---

### Post by tonysathre on 2005-12-10
[QUOTE=Thunk]But is it possible for XP to handle a secondary FAT32 partition (not the one it's installed on)?[/QUOTE]

yes XP can handle it just fine, u can use disk management to create and format them

---

### Post by ren wins on 2005-12-10
i found a program in synaptic that looked like it could let you read/write ntfs
as well as repair tools to run after you wrote to ntfs from linux

i forget it's exact name, but if you have all your repositories turn on, you should be able to find it if you search synaptic for ntfs

---

### Post by tonysathre on 2005-12-10
i think your talking about the NTFS Project, i think the toolset is called ntfstprogs

---

### Post by ren wins on 2005-12-10
that sounds familiar, it's good to know it's in synaptic tho, eh?

---

### Post by tonysathre on 2005-12-10
ya i havent tried it but i think i might, let us know how well it works and if there were any problems

---

### Post by varunus on 2005-12-10
Guys, don't try to write to NTFS from linux using the stuff included in Ubuntu.  You will run into problems, and corruption.

There is currently only one project that lets you write to ntfs in linux.  It is called Captive, but has not been developed for a while.  I've heard reports of people getting it to work on Ubuntu, but I've never seen it...You guys could try looking it up.

---

### Post by ren wins on 2005-12-10
i never bothered trying it
i've got enough HD space that i dont need to use my windows partition for anything but running windows
and i store stuff on fat32 partitions

---

### Post by kroiz on 2005-12-10
dont forget that FAT32 has some serious draw backs, the most serious one for me was that the max file size is 2 GB (or is it 4 not sure anymore) that is a big problem when working with video from digital camera that tends to be like 10 GB for an hour.
so only swith your windows to FAT if you are not using it for home video capturing and making DVDs

---

### Post by fate on 2005-12-10
For those wanting to format a FAT32 for WinXP -- yes, you can install WinXP on a FAT32, yes it will write flawlessly to other FAT32 partitions. You must keep your partition below 32000mb (32gb). When installing XP on a new drive (or simply deleting an old partition), just select 'C' for creating a new partition and type 31000 or 32000 at the following screen and you'll be given an option to format this partition as NTFS or FAT32.

I usually have WinXP installed on a 25gb NTFS partition -- this way, I have enough space to load my games but nothing too overbearing. Since I only use WinXP for a gaming platform anyway and not a backup (backup data is on a linux partition), this combination seems to work well for me.

I'm running 2 120gb drives, btw.

---

### Post by aysiu on 2005-12-10
[QUOTE=fate]You must keep your partition below 32000mb (32gb).[/QUOTE] I don't know if that's the official line, but I do know that I successfully had a 100 GB FAT32 partition that I shared between XP and Linux for a good six months with **no** problems.

As for the earlier post, it's a 4 GB file size limit (not 2 GB).

---

### Post by ren wins on 2005-12-10
i've got 4 40gb fat32 partitions, and there's no problem with them

---

### Post by penvzila on 2005-12-10
[quote=IdolizingStewie]You need to put text between the URL tags for the link to show up. I didn't realize you'd answered your question until I quoted it. [penvzila's link to Explore2fs.]("http://uranus.it.swin.edu.au/%7Ejn/linux/explore2fs.htm")[/quote]

I removed it because it doesn't actually do what I was thinking.

---

### Post by penvzila on 2005-12-10
I've had some success using this tool (it's early yet thought)

[http://www.it.fht-esslingen.de/~zimmerma/software/ltools.html](http://www.it.fht-esslingen.de/~zimmerma/software/ltools.html)

---

