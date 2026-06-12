---
title: "I'm a bonehead."
date: 2011-07-06
forum: Desktop Environments
---

### Post by ben44b on 2011-07-06
It's true. I admit it.

I have WUBI installed with Windows and Ubuntu 11.04. I was reading up on BURG and thought I would give it a whirl. Bad idea.

Now I get a black screen on booting with an error: device not recognized (long chain of letters and #s)

These are the three lines I added to install burg according to the help page:
sudo add-apt-repository ppa:n-muench/burg

sudo apt-get update && sudo apt-get install burg

and then:

sudo burg-install "(hd0)"

Can I reverse this boneheadedness?


Thank you.

---

### Post by HeadHunter00 on 2011-07-06
> **ben44b said:**
> It's true. I admit it.

I have WUBI installed with Windows and Ubuntu 11.04. I was reading up on BURG and thought I would give it a whirl. Bad idea.

Now I get a black screen on booting with an error: device not recognized (long chain of letters and #s)

These are the three lines I added to install burg according to the help page:
sudo add-apt-repository ppa:n-muench/burg

sudo apt-get update && sudo apt-get install burg

and then:

sudo burg-install "(hd0)"

Can I reverse this boneheadedness?


Thank you.
yes, ofcourse. thats what linux is all about. anyways, first thing you need to do is get you bootable ubuntu cd or usb. boot into the cd, and fire up the live ubuntu session. open up the terminal and then run: sudo grub-install '(hd0)'
i ran into this kind of problem a thousand times myself. Just don't call yourself a bonehead my friend.

---

### Post by ben44b on 2011-07-06
Thanks for the help.

When I entered that line in the terminal I got this:

```
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```


?
Don't know.

---

### Post by ben44b on 2011-07-06
My live CD is 10.04. Does this make a diffrerence?

---

### Post by bcbc on 2011-07-06
With Wubi you need the windows boot loader. See the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") Problem #1 Solution #1 or #2 on how to repair the MBR.

---

### Post by ben44b on 2011-07-06
Thanks.

How do I find out which sd? is my Windows drive?

---

### Post by dFlyer on 2011-07-06
> **ben44b said:**
> My live CD is 10.04. Does this make a diffrerence?

Your live cd needs to be the same version as you have installed. According to your first post it's 11.04 so that is the live cd you will need.

---

### Post by ben44b on 2011-07-06
> **dFlyer said:**
> Your live cd needs to be the same version as you have installed. According to your first post it's 11.04 so that is the live cd you will need.

Does this mean that I should avoid the Wubi Megathread and just download the a new ISO with 11.04?

Thx

---

### Post by bcbc on 2011-07-06
> **ben44b said:**
> Thanks.

How do I find out which sd? is my Windows drive?

hd0 = /dev/sda

If you want, post the output of "sudo fdisk -l" (lower case L)

---

### Post by ben44b on 2011-07-06
> **bcbc said:**
> hd0 = /dev/sda

If you want, post the output of "sudo fdisk -l" (lower case L)

```
ubuntu@ubuntu:/etc$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdf1cf9ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1785    14336000   27  Unknown
/dev/sda2   *        1785       77826   610793472    7  HPFS/NTFS
ubuntu@ubuntu:/etc$ 


```

---

### Post by ben44b on 2011-07-06
OK. Followed the Wubi Megathread and miraculously things are back to normal.

I guess I should install Ubuntu on a partition of its own like bcbc suggested. My question is can I still choose which OS will come up after I do this?

Thank you for the help all.

---

### Post by bcbc on 2011-07-06
> **ben44b said:**
> OK. Followed the Wubi Megathread and miraculously things are back to normal.

I guess I should install Ubuntu on a partition of its own like bcbc suggested. My question is can I still choose which OS will come up after I do this?

Thank you for the help all.

Yes. You can choose. 

Here's a decent guide [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html) (I think it's mostly for 10.10).

This particular one shows how to partition manually first. [http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Then you can either install fresh afterwards or [migrate your current wubi]("http://ubuntuforums.org/showthread.php?t=1519354").

PS any partitioning carries some risk - so backup first e.g. create windows repair cd / system image / backup data

---

