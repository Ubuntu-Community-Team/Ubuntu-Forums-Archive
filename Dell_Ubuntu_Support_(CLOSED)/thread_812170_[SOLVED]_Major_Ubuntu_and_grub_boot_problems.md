---
title: "[SOLVED] Major Ubuntu and grub boot problems"
date: 2008-05-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shortylonglegs on 2008-05-29
I really need help, I am working on a final project for calculus due tomorrow and my computer won't work.  I was working with openoffice spreadsheet and had firefox open to pandora.com.  I plugged in my flashdive and tried to open a file from it in openoffice.  The music suddenly stopped and the system didn't respond to anything.  I had to do a hard reboot, and when I did all that comes up is an error about the OS not loading.  Usually it goes to grub, because I dual boot with XP, but not even grub came up.  I tried using my live CD to run fsck, because that worked before, but nothing happens now:

> ubuntu@ubuntu:~$ sudo fsck -V /dev/sda3
fsck 1.40.8 (13-Mar-2008)
[/sbin/fsck.ext3 (1) -- /dev/sda3] fsck.ext3 /dev/sda3 
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda3: clean, 156194/612000 files, 964035/2441880 blocks (check in 5 mounts)

I urgently need to finish this project and can't effectivly do it from this live CD.

---

### Post by Bakon Jarser on 2008-05-29
Try this.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Jose Catre-Vandis on 2008-05-29
What exactly is the first error on boot (where you are expecting grub) ?

Perhaps try a forced fsck line:

```
(sudo) e2fsck -f /dev/sda3
```

or a more detailed one
```
e2fsck -C0 -p -f -v /dev/sda3
```

Could also be that grub is in a mess. Try re setting grub using live CD:
Open terminal
sudo grub
find /boot/grub/stage1
root (hd?,?)  <- as found in above
setup (hd?)
quit
reboot

---

### Post by shortylonglegs on 2008-05-29
Thanks so much for the prompt replies, that worked.
Saved me a lot of effort and panic.

---

