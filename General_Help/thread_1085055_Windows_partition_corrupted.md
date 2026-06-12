---
title: "Windows partition corrupted?"
date: 2009-03-02
forum: General Help
---

### Post by President_Thor on 2009-03-02
Alright, so I use a laptop with both Xubuntu 8.10 and Windows XP  Pro installed. I'm normally using Windows because I need iTunes for my phone, and a couple things for school. Both operating systems are partitioned on the same physical drive. 

Yesterday, I booted into Xubuntu for the first time in a while so that I could check and see if something I had was compatible with it. I stumbled into the StartUp-Manager, but I don't recall changing anything. After I restarted to boot into Windows, it had vanished from my list in GRUB.

If I run GParted, I can see that the partition isn't mounted, and it won't mount... I can, however, see how much free space I have on the drive (if that helps?) If I run ntfsfix for the partition, I get this.

"Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk."

The only way I know of to run check disk is within Windows... which I can't get to.

---

### Post by taurus on 2009-03-02
How did you run ntfsfix?  Did you remember to include the sudo in front for root privilege?

---

### Post by bodhi.zazen on 2009-03-02
Boot xubuntu

At the grub screen press the escape key

That should then give you a full menu where you can select Windows.

---

### Post by President_Thor on 2009-03-02
Now I feel stupid.... I've been using Linux for several years. I may not be an advanced user, but I should have known to run it as root.

It said it fixed it, time to reboot and see if it worked.

josh@ASGARD:~$ sudo ntfsfix /dev/sda2
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda2 was processed successfully.

---

### Post by President_Thor on 2009-03-02
> **bodhi.zazen said:**
> Boot xubuntu

At the grub screen press the escape key

That should then give you a full menu where you can select Windows.

Um... GRUB kind of loads before Xubuntu does? When should I try pressing escape, because Windows still isn't in the list?

---

### Post by President_Thor on 2009-03-02
BUMP

Sorry, but it's kind of important.

---

### Post by bodhi.zazen on 2009-03-02
As you computer is booting

First you see the bios

Then you get the grub screen. The grub menu is "hidden"

You see a brief message "press esc to view the menu" or some such

At that menu, press the esc key ;)

If you miss it, the boot process will continue booting Xubuntu and you are too slow with the esc key ;)

---

### Post by President_Thor on 2009-03-02
Um... I actually get a list of OSes for 15 seconds before I boot into Xubuntu. XP vanished from the list. Am I supposed to press escape before that, or is that the menu you're referring to?

---

### Post by bodhi.zazen on 2009-03-02
That is it.

15 OS, :lolflag:

Well sounds like you will have to manually add in windows then.

You can also try the supergrub disk.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

```
[COLOR=Black]_[]("http://users.bigpond.net.au/hermanzone/p15.htm#windowstitle")_[/COLOR]title  Windows
root  (hd0,0)
makeactive
chainloader  +1
boot
```

change "hd(0,0)" to your windows partition.

---

### Post by President_Thor on 2009-03-02
lol

That's actually what I was in the process of doing.

I can't remember how to find the location of the partition. I think it's (hd0,2), but I can't remember. I know I've done it once before, and there's a command to find it.

---

### Post by bodhi.zazen on 2009-03-02
```
sudo fdisk -l
```

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by President_Thor on 2009-03-02
Thanks.
Yeah, I was right.

---

### Post by President_Thor on 2009-03-02
Thanks.

I've got Windows up and running now. All it took was me scanning it in Xubuntu, re-adding it to my grub menu.lst, and then running check disk at Windows' start up.

---

### Post by dragos240 on 2009-03-02
See the problem i had, my hardrive was corrupted as well,
[http://ubuntuforums.org/showthread.php?t=1027020](http://ubuntuforums.org/showthread.php?t=1027020)

---

### Post by absolutezero1287 on 2009-03-02
To make it easier in the future....

```
sudo gedit /boot/grub/menu.lst
#hiddenmenu
#remove the comment from the above line
#to hide the menu
timeout 3
#change the number to make the menu appear longer

```

---

### Post by absolutezero1287 on 2009-03-02
> **President_Thor said:**
> 
I can't remember how to find the location of the partition. I think it's (hd0,2), but I can't remember. I know I've done it once before, and there's a command to find it.

```

sudo grub
find /boot/grub/stage1

```

---

