---
title: "Installation slow at 6%"
date: 2006-01-01
forum: General Help
---

### Post by JGO on 2006-01-01
Hello All,
     When trying to install Ubuntu or Kubuntu for whatever reason it crawls to a halt when it reaches 6%. It is still working .... just taking literally like 5 mins for each little file to get copied. After four hours of waiting ... it is still at 6%, but isn't frozen up, just REALLY SLOW.

I have searched the forum and noticed other people posting of the same issue, however no clear cut solution for it.

**_Here is what I have tried/checked:**_

**CD's:**
Downloaded and checked MD5 for both Kubuntu and Ubuntu.
Both are burned to plain CD-R using OS X disc utility.
Both boot fine and act fine until 6%.

**CD Drive:**
Drive works for everything else just fine, literally. Pioneer DVR-104.
Set as master on second IDE chain. The only device on that chain.
Checked BIOS, it is set as 'ATA-33'.
Swapped it out with a "super drive" (Apple Pioneer drive), same issue.

**System specs:**
Asus 87N8X
Athlon XP 3200+
1 GB PC3200
AGP GeFroce 6800
80 GB IBM IDE HDD
Pioneer DVR-104 DVD-R

Any information would be appreciated, I am going to start tinkering with BIOS settings related to the drives in hopes I will find something.

Thanks.

---

### Post by Omnios on 2006-01-01
Counts on the speed of your computer, tryed to install it on a p2-350 and it took almost half a day till it failed. 
 
 Some of the bigger sections can take quite a while just check your hard drive light and if its going it should still be loading.

 I think its because certain parts of the install are pretty big

---

### Post by nix4me on 2006-01-01
On that machine, install should fly.  Something is amiss with your hardware or media.

nix4me

---

### Post by JGO on 2006-01-01
Thanks for the replies.

I don't think the computers speed is the issue frankly. Also as for the media I am just using imation CD-R's ... I think it is a hardware problem, but I don't feel my hardware is malfunctioning, as this combination of hardware works fine for a Windows and Gentoo install on another hard drive.

So I suspect (I know nothing of it really.) That there is some sort of setting that changes during the install. The reason I say this is that it works fine up until that point and I am not the only one to notice this issue.

So off to messing around with DMA settings etc... etc...

---

### Post by JGO on 2006-01-01
Ok well after changing all DMA/LBA/CHS settings on the CD-ROM ... no luck, 6% is still where it gets slow.

Ironically the Ubuntu 5.04 works fine.

On a different note, can I install 5.04 and then upgrade to the current version?

Thanks.

---

