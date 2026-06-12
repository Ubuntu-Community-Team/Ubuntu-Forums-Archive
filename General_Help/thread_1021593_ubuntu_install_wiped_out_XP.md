---
title: "ubuntu install wiped out XP"
date: 2008-12-25
forum: General Help
---

### Post by flattop1 on 2008-12-25
So I've been using Ubuntu for a month or so (live cd) and decided to install it today.
I was going to do a dual boot so I chose the guided install and partition manager said it was going to install Ubuntu in the free space leaving 39% windows XP.. and 61% Ubuntu.
So I clicked continue

Anyway an hour later I came back in and the partition manager was still at 0% ....so I clicked cancel...Now the computer wont boot up in XP and when I try and see the hd from the ubuntu live disk it appears that windows is gone?
 Is there any way to recover this disk because I had photos which cant be replaced?

---

### Post by wolfen69 on 2008-12-25
first off, you may have learned a hard lesson. BACKUP, BACKUP, BACKUP! (i lost 35,000 mp3's because of stupidity)

next, pop in the live cd and ```
sudo su
``` then post the output of ```
fdisk -l
```

---

### Post by caljohnsmith on 2008-12-25
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by flattop1 on 2008-12-25
OK thanks guys for the replies.
First of all,I figured it out..
The files were not wiped after all.From the linux cd I kept getting a mount error for the windows files and I panicked...and thought everything was gone.It sure looked that way to a newbie like me anyway.
Anyway after removing the live cd and rebooting to windows (the reboot took ages for some reason)I was glad to find that everything was intact.
So I **backed up** everything to a dvd and now I am trying to set up a dual boot with Ubuntu.
(I would probably just erase windows but the wife is not convinced yet..so in the meantime were going for a dual boot)
But the install keeps failing at the "resize partition" stage.It just seems to sit there and never actually resizes the partition and eventually says "partition failed!
Any help would be great.

---

### Post by oilchangeguy on 2008-12-25
glad you were able to get your data. what are the specs of your computer? cpu speed, amount of ram, and hard drive size?

---

### Post by albinootje on 2008-12-25
> **flattop1 said:**
>  But the install keeps failing at the "resize partition" stage.It just seems to sit there and never actually resizes the partition and eventually says "partition failed!

Try the resizing with the gparted live cdrom :
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

