---
title: "KDE locked me out of my own computer!"
date: 2009-02-09
forum: General Help
---

### Post by Shadow12313 on 2009-02-09
I recently installed KDE and now it will not let me login.  Every time I try it says "login failed".

Any ideas?

---

### Post by taurus on 2009-02-09
At the GUI login screen, press <Ctrl><Alt>F2 to get to another console.  Now, are you able to log in with your username and passowrd?

---

### Post by Shadow12313 on 2009-02-09
That is the console login right?
If it is I have already tried that and it works fine.

---

### Post by taurus on 2009-02-09
Then look at the permissions/ownership of your $HOME.

```
ls -la ~ | more
```
Hit the space bar for the next 24 lines.

Check your disk space too.

```
df -h
```

---

### Post by Shadow12313 on 2009-02-09
Could the disk space be a problem?
Since I am in XP right now I have to reboot each time I want to type in a command.

---

### Post by Shadow12313 on 2009-02-09
I typed in the fd -h command and it came back with this:

"13g 13g 0 100% /"
and more.

---

### Post by taurus on 2009-02-09
> **Shadow12313 said:**
> I typed in the fd -h command and it came back with this:

"**[COLOR="Red"]13g 13g 0 100% /[/COLOR]**"
and more.

So, looks like you have maxed out your root partition--/.  Log in from a console and run

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```
That should buy you some space to log into KDE.  Don't forget to empty your trash bin since files in there are taking up valuable space.

---

### Post by Shadow12313 on 2009-02-10
Thanks it worked!  Is there anyway to increase the size of the root partition?  I still have +90GB of free space on my harddrive.

---

### Post by taurus on 2009-02-10
It depends where that 90GB free space is located.  Is it just in front or after Ubuntu root filesystem?

```
sudo fdisk -l
```

---

### Post by Shadow12313 on 2009-02-14
It says this:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee81ee81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 2006 MB, 2006974464 bytes
16 heads, 32 sectors/track, 7656 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16        7656     1955904    e  W95 FAT16 (LBA)

---

### Post by hyper_ch on 2009-02-14
you used wubi to install linux?

---

### Post by Shadow12313 on 2009-02-14
Yes I did, why do you ask?

---

### Post by hyper_ch on 2009-02-14
you can't expand it in wubi - at least as far as I know...

so you're approach is to kill that installation and then do another wubi install or real install.

---

### Post by Shadow12313 on 2009-02-14
I just reinstalled Ubuntu through wubi yesterday.  Is there any other way to expand it without reinstalling again?

---

### Post by hyper_ch on 2009-02-14
not that I know of
with a real install on a real partition it would be possible...

but then, you have enough space to make a backup? if so re-setup is quite simple

---

### Post by Shadow12313 on 2009-02-14
If I install it using the cd will I be using grub?

---

### Post by hyper_ch on 2009-02-14
not sure what you mean...

---

### Post by Shadow12313 on 2009-02-14
Since I installed it using wubi it doesn't seem to be using grub.

---

### Post by hyper_ch on 2009-02-14
no clue about wubi install... never used it, only read that you can't expand later on.

---

### Post by Shadow12313 on 2010-04-12
I have completed a real install now after using wubi for a while later.

---

