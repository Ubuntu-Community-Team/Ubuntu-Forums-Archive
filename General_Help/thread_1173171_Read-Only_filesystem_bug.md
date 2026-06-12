---
title: "Read-Only filesystem bug"
date: 2009-05-29
forum: General Help
---

### Post by perigee on 2009-05-29
I'm using Jaunty for a while. It's just fine at beginning, but now. The problem is that I'm using ext4 on Jaunty version, my home directory became suddenly read-only, all directories became read-only. I don't know how to resolve this problem. Anyone has any idea?

---

### Post by iponeverything on 2009-05-29
Looks like you might not be the only one. I would open a bug report in lauchpad.

[https://answers.launchpad.net/ubuntu/+question/72575](https://answers.launchpad.net/ubuntu/+question/72575)

---

### Post by upbeat.linux on 2009-05-29
Good find iponeverything.  

On LinuxQuestions its suggested that forcing a file system integrity check, doing a manual fsck, then remounting the drive

```
mount -n -o remount /
```

corrects the issue. The manual fsck as root worked for me.

If its only an issue with your home directory you can reset permissions by going to the prompt and typing:

```
sudo chmod -R 700 /home/username
```

Replace username with your username.

---

### Post by perigee on 2009-05-29
fsck seams work for me, it's found an error of my harddisk. Waiting to see if it does really resolve my problem ... Thanks a lot.

---

### Post by perigee on 2009-05-29
my system is just crashed after fsck, it gave me a GRUB Error 17, couldn't find filesystem :-( downloading live CD to rescue ...

---

### Post by perigee on 2009-05-29
Never execute fsck on a mounted partition, i've just made this big mistake and crashed my system.

---

### Post by upbeat.linux on 2009-06-01
Oh man! I'm terribly sorry.  I should have specified that you boot into rescue mode or force fsck on next boot. My sincere apologies.  Sometimes simple steps slip my mind when posting to forums.

usb drive fsck:

```
sudo e2fsck -C0 -p -f -v /dev/sdb1
```

For a specified mount:

```
init 1
umount /dev/sda
fsck /dev/sda3

```

you can also do something like:

```
sudo touch /forcefsck
sudo reboot
```

or even

```
shutdown -F now
```

---

### Post by ActiveFrost on 2009-06-01
The same for me, though, not for my home directory - got my USB Flash drive formated to read-only ( and the best part is that I wasn't able to chmod it .. needed to format it :( ).

---

