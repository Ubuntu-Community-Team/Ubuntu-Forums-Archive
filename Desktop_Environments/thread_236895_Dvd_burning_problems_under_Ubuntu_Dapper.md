---
title: "Dvd burning problems under Ubuntu Dapper"
date: 2006-08-15
forum: Desktop Environments
---

### Post by cborga1985 on 2006-08-15
I have all the dvd tools and growisofs and all the other dvd stuff installed but when I go to burn a dvd with gnome baker. I get the following error in the output.

> Executing 'builtin_dd if=/home/boston/Desktop/Home/dvdripping/LARRY_INSPECTOR.ISO of=/dev/hdd obs=32k seek=0'
/dev/hdd: "Current Write Speed" is 1.0x1385KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

anybody have any idea why this is happening? I'm using memorex dvd-r's which worked fine under windows but I really don't want to dual boot just to burn dvd's. When I start to burn it acts liek it's burning rfor a second then ejects the dvd and when I reinsert it naultils shows it being blank so it didn't even write to the dvd. I suspect there is a permissions problem but I don't knwo how to fix that.
My first dvd burner is at /dev/hdc and second is located /dev/hdd and both say that dma is enabled. Any help would be much appreciated.

---

