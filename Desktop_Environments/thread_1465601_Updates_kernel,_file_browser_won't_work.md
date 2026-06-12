---
title: "Updates kernel, file browser won't work"
date: 2010-04-29
forum: Desktop Environments
---

### Post by billwww on 2010-04-29
I just updated to the 2.6.31-21 kernel in ubuntu 9.10 and the file browser no longer opens. I get the spinning busy cursor for about 15 seconds and then nothing. Other programs work: I can use the file managers in gedit and openoffice.org, but none of the folders on the drop-down menu under "Places" will open.

System: Gigabyte GA-7VAX motherboard with Athlon 2500+ processor (32 bit), Radeon 9600 video card, 160 GB RAID 1 array (not used by ubuntu) + 160 GB (used by ubuntu). RAID array is dead WinME (that's a long story).

I'd appreciate some ideas. Thanks,
billwww

PS: I notice 2 copies of "AT SPI Registry Wrapper" in Startup Programs (also 2 missing icons on desktop).

---

### Post by billwww on 2010-04-30
I have more info on this problem. After a failed startup, I ran fsck manually (as suggested) to try to fix the file system. This yielded the following information:

init mountall main process failed terminated with status 3
mount of filesystem failed
unconnected directory inode 1605674 (/tmp/???)

I tried the manual fixes, and the computer did start up, but with the same problem--no file browser. My spouse's login works normally (file browser operational). She says she deleted one of the missing icons while using my login. The other icon was for an incomplete attempt to install a windows game under Wine. I recall that a recent update included a new version of Wine, though this seems like a long shot.

I have backed up my spouse's files, but I can't back up my own without the file browser. My only option may be to remove the drive and use another computer to access the file system (if it can).

I used the ubuntu 9.10 live CD to test the disk, which checked out ok.

---

