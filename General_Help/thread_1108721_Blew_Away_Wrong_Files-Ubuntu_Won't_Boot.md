---
title: "Blew Away Wrong Files-Ubuntu Won't Boot"
date: 2009-03-28
forum: General Help
---

### Post by waltkerr on 2009-03-28
After using Ubuntu 8.10 for about four months and loving it I encountered a full hard disk situation. I was carefully erasing log files and other "uneeded" stuff trying to recover some disk space. I blew
away some critical files in the Boot directory (abi.2.6.27, config-2.6.27, System.map.2.6.27, vmcoreinfo.2.6.27) and now cannot boot into Ubuntu. I can start from the Live CD into the generic
Ubuntu user account but my former user account is not accessible. I don't want to re-install Ubuntu because that would most likely wipe out my Documents, Pictures, and Music folders.
I know my personal files are still on the hard disk. Is there some way of accessing them so I can copy them to my second hard drive before I re-install Ubuntu? I've tried finding my
former user account using the Unix terminal but I don't see it on the disk. Am I really up the creek here??? Thanks for any suggestions.

---

### Post by lykwydchykyn on 2009-03-28
You can fix this from the liveCD, but it involves some command-line stuff.
 - Boot to the CD
 - Open a terminal and become root with "sudo -s"
 - Mount your root partition on the hard drive; if it's sda1, for instance:
```

mkdir /media/sda1 && mount /dev/sda1 /media/sda1

```
 - Change to the new directory, and do the following:
```

cd /media/sda1
mount --bind /proc /media/sda1/proc
mount --bind /dev /media/sda1/dev
chroot ./

```
Now, this puts you in your root partition environment.  So until you type "exit", any commands you type will be as though you're running them on your hard drive install.  So run this:
```

aptitude reinstall linux-generic

```
Then exit and reboot.

---

### Post by pbpersson on 2009-03-28
> **waltkerr said:**
> 
I know my personal files are still on the hard disk. Is there some way of accessing them so I can copy them to my second hard drive before I re-install Ubuntu? 

In case you cannot get Ubuntu re-installed using the commands posted by the last person, I would think you could easily boot into the Live CD, mount both your hard drives, and copy the data you want to save from one to the other.

---

### Post by waltkerr on 2009-03-28
Thank you both for your suggestions. I was able to mount sda1 and see the original files which I backed up and then re-installed Ubuntu.

---

