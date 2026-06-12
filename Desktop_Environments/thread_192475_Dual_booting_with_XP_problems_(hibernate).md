---
title: "Dual booting with XP problems (hibernate)"
date: 2006-06-08
forum: Desktop Environments
---

### Post by jakev383 on 2006-06-08
Here's a weird one for you, which I hope somone has come across the answer to (if I find it, I'll post it!). 
I'm dual booting with Windows XP Media Center edition (on my laptop). I have my FAT32 partition shared:
/dev/sda7    vfat rw,users,gid=users,umask=0002,uid=1000,utf8=true,exec,dev,auto 0 0
Now here's the weird part. If I create a folder in XP and then hibernate, start back up in Ubuntu, I can see the folder. If I create the folder in Ubuntu then hibernate, un-hibernate XP, the folder is not there. If I reboot XP, then I can see the folder, but not until that point. I know this will probably be more of a XP question that a Linux one, but I was hoping that someone else who has dual-booted has found the same problem and found a solution.
Thanks

---

### Post by fmo on 2006-06-08
Hi jakev383,

When resuming you hibernation in XP, have you tried to kill the "explorer.exe" process and relaunch it?

---

### Post by jakev383 on 2006-06-12
[QUOTE=fmo]Hi jakev383,

When resuming you hibernation in XP, have you tried to kill the "explorer.exe" process and relaunch it?[/QUOTE]

That didn't do anything, thanks though.
I've looked into it further, and it seemed that every time I create a dir/file in Linux, hibernated, booted to XP, the dir would not be there. Next time I booted XP, it complained about errors on the drive. I tried this twice, and it seemed that everytime I created a file/dir on the FAT32 drive in Ubuntu, it caused errors on the drive. I've been playing with my fstab to try and fix this, and I *THINK* I may have found a solution to my dilema. I'll edit this and post my fstab when I boot back to Linux.... I think it had to do with using utf=8 and other options like that.

---

### Post by frying_fish on 2006-06-12
I had a similar thing with ext3, I think its because when it hibernates it sets flags to store the state, and thus booting to the other os won't allow you to modify those yet I am only guessing though.

---

