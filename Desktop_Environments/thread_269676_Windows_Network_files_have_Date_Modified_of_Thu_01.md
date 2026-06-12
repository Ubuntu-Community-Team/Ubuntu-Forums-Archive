---
title: "Windows Network files have Date Modified of Thu 01 Jan 1970"
date: 2006-10-02
forum: Desktop Environments
---

### Post by pdc4342 on 2006-10-02
I am a newbie to Ubuntu and have a problem which I can not find a solution to in the conferences or by Googling although it seems fairly basic.

I have four machine, two dual boot with Ubuntu and two with Windows XP only linked via Ethernet and WiFi. I have Samba installed. Dual boot machines have common drives reformatted to FAT32. I can access these drive OK.

However when I look across the network from a Ubuntu machine to a Windows machine in Nautilus all the folders and files have a date modified of Thu 01 Jan 1970 and if I copy them onto my local machine they still have that date. If I then copy them back the date is blank when viewed under Windows. If however I 'push' them from a Windows machine to the Ubuntu machine that is fine and the dates are transfered as I move files back and forth. This is the same on both Ubuntu machines and Windows machines. The permissions look reasonable but I can not change them although I seem to be the owner

Is this to do with permissions and how do I fix it please? 

For reference I have also had to fix the known problem of the breaking s91samba links in rc2.d and rc3.d on both machines but I can not see any way that is related.  

Any suggestions appreciated please.

---

