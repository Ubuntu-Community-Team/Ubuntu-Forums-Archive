---
title: "Mount Mistake - Drive contents now on desktop"
date: 2009-02-05
forum: General Help
---

### Post by sskye on 2009-02-05
This on 8.04:

I did something pretty stupid - I was trying to mount an NTFS external drive, and was getting an error message ("directory does not exist") when typing in the suggested force mount command. I later found out that that command was actually working, despite the error message.

So, I decided to change the directory it was mounting to:
```
sudo mount -t ntfs-3g /dev/sdb1 /home/****/Desktop -o force
```

This worked! Unfortunately, it also mounted all the folders and files on the drive to my desktop. Oops. So, I decided to restart and unplug the drive. When I logged in again, I found the contents of my /home/****/ folder were now mounted to the desktop, and what was previously the desktop is now just a folder. The "Home" icon has disappeared from the file browser sidebar, though clicking on "Desktop" brings me to the folder.

What can I do to restore it to how it should be? This is the result from mount:
```
****@GLaDOS:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/****/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=****)
```

I don't see anything "mounted" to the desktop, nor any binds. Anyone know better than I do?

---

### Post by juniord2016 on 2011-11-06
Dear Helpers
    Hello, actually I have to say. I thought I was the only man in the wide world to do such silly thing. I did exactly the same thing and I restarted the computer. What I saw every time I switched on my computer was 'drive Freecom HDD is not ready'. I need to fix this, but my desktop file is OK after restarting. That's the only abnormal thing about my system. Thank you

    Regards

---

