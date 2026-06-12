---
title: "Black screen can’t login"
date: 2021-03-20
forum: Desktop Environments
---

### Post by devdlp on 2021-03-20
So I’m writing this from my phone because my desktop which runs Ubuntu 20.04 is locked up or something. Ever sense I made my HDD (I have a ssd and hdd) auto boot I haven’t been able to get in. Crtl + alt + F1 does not work. It does nothing. I press enter then my password to see if it lets me in through the dark and nothing could somebody come by and save the day please

---

### Post by CelticWarrior on 2021-03-20
> [COLOR=#000000]Ever sense I made my HDD (I have a ssd and hdd) auto boot I haven&#8217;t been able to get in.[/COLOR]
Please describe what you did or what you mean by this statement.
At first glance, making a drive "auto boot" doesn't make sense but only you can tell us what really happened.

---

### Post by devdlp on 2021-03-20
I first set my hdd to auto boot then played around with pulseeffects. Restarted. Then after the hp screen when you boot I don’t see Ubuntu logo on either screen. So I press enter blindly and enter my password. Like I said at the top I tried crtl +alt+f1 nothing happens. That’s it. Also I tried taking out the hdd to see if it would boot but no it didnt

---

### Post by grahammechanical on 2021-03-20
If the Ubuntu operating system is on the ssd and the boot priority in the UEFI settings is given to the hard drive, then Ubuntu will not load. If there is no operating system on the hard drive or it is broken, then you may get such a black screen.

Regards

---

### Post by devdlp on 2021-03-20
So what should I do

---

### Post by devdlp on 2021-03-20
Sorry I’m at work right now can’t respond as fast

---

### Post by devdlp on 2021-03-20
Should I take out the hdd and keep the ssd in?

---

### Post by CelticWarrior on 2021-03-20
First you need to confirm what you really did and why.
I suppose [post#4]("https://ubuntuforums.org/showthread.php?t=2459534&p=14027437#post14027437") has the correct idea but if so you need to describe exactly what happened and why you tough that changing the boot order was a good idea and exactly what were you trying to achieve with that change.

Considering the history of your posts here it seems you lack basic understanding about basic stuff, difficulties to express yourself in a clear understandable way, or both. So we must thread very carefully with any suggestion, better to gather all the relevant data beforehand to assure we understand the problem and then propose some sort of solution confidently.

---

### Post by devdlp on 2021-03-20
I never tried to change the boot order I just wanted the hdd to auto boot

---

### Post by CelticWarrior on 2021-03-20
> **devdlp said:**
> I never tried to change the boot order I just wanted the hdd to auto boot
Again, what does that mean? What did you do exactly? For what purpose?

---

### Post by devdlp on 2021-03-20
I went to disk app in Ubuntu gnome 20.04 and clicked on the hdd which is just for storage not the os and clicked a button that said auto then restarted and nothing after that

---

### Post by devdlp on 2021-03-20
Sorry still at work hard to respond but I did it because I wanted the hdd to auto boot at startup because that’s where my steam games go

---

### Post by CelticWarrior on 2021-03-20
So, probably (still guessing here), you mean **auto mount**? That would be boring trivial with Disks > edit mount points.
But, again, in order to help you we need to know EXACTLY what you did.

---

### Post by devdlp on 2021-03-20
Yes auto mount. There was a button, the first button at the too left it said default or something i unchecked that and it unlocked auto mount that’s all

---

### Post by CelticWarrior on 2021-03-20
Please... Really... I'm sure you know that we didn't see what you did so, please, whenever you're ready, describe what you did in a way a normal person can understand. Don't say "the first button" (where? what button?) or the gibberish that followed.

---

### Post by devdlp on 2021-03-20
I said the very first button in the disk manager idk the name but it was the first one after you click options on a hdd....in disk manager

---

### Post by devdlp on 2021-03-20
I know I messed up and it’s my problem and I’m sorry for frustrating you but could you please speak a little bit nicer

---

### Post by devdlp on 2021-03-20
I came here for help you know and thank goodness for @grahamm but with you I feel dumber than I already thought I was man cmon

---

### Post by BFG on 2021-03-21
> **devdlp said:**
> Should I take out the hdd and keep the ssd in?
Keep both SSD and HDD in.

Make a ubuntu LiveUSB on another system and boot your system from the USB.
Once running, download boot-repair into the live USB session.
[https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)   *

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update

Run the boot-repair, it will probably fix.


(* Note- You can get pre-build ISOs with boot-repair, avoid them. Above is superior.).

---

### Post by devdlp on 2021-03-21
Sorry i was asleep. So i fixed it by disabling legacy. but nvidia wasnt installed anymore and a couple other things so i just started fresh with ubuntu 20.10.
My question is what can i do to get my second hdd to auto mount without it turning my login screen black and not allowing me to log in or do i have to make a new thread?? also and thank you @BFG

---

### Post by ActionParsnip on 2021-03-22
Sure what file system(s) does it use?
What is the output of:
```

sudo parted -l; mount

```

---

### Post by BFG on 2021-03-24
> **devdlp said:**
> .....what can i do to get my second hdd to auto **mount**......

Mount and boot are very different things.  You would only want to boot the HDD if it contained an alternative operating system, e.g. windows.  If your HDD is just an extra storage drive and you try and make it boot then your system will look for an operating system on it at start up, fail to find one and you'll get a black screen.

If you just want to use it for data and storage, then mount is the correct term.

Mounts are best handled in the /etc/fstab file
If you're going to use links to games for a Steam app you need a durable mount. 


Create a directory in the OS for the disk to mount to. By convention this is something in /media

```
sudo mkdir -p /media/myhdd
```

Then find the UUID of the partition on the drive you want to mount.  

```
lsblk -f
```

Or if you prefer a GUI method you can use gparted

The UUID will probably be a long number like b425e7f5-1f06-4650-83b9-9964675486ec, put in the XXXXXXX position below


edit /etc/fstab and add a line that mounts the HDD. Using the following syntax:

```
UUID=XXXXXXX     /media/myhdd          ext4    relatime,errors=remount-ro 0       1
```


ext4 is the file system type for a hdd that was formatted in linux.  If the drive is empty go for ext4, if it's already got data from e.g. windows, you'll need to match with vfat or ntfs instead.

Just google fstab for more info.

Once you've edited:
```
sudo mount -a
```

The drive should be available.  You'll then need to set permissions for your user account on the drive.

---

### Post by BFG on 2021-03-24
> **devdlp said:**
> I came here for help you know and thank goodness for @grahamm but with you I feel dumber than I already thought I was man cmon
You probably want to choose a username that doesn't have "dev" in it.    And dlp is data loss prevention. It makes you sound like you should already be an expert. ;)


Especially because some people either can't read or are weak at making allowances....
> **devdlp said:**
> ......I’m writing this **from my phone**.........

---

