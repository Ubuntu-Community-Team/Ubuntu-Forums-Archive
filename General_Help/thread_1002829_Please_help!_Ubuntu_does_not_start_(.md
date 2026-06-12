---
title: "Please help! Ubuntu does not start :("
date: 2008-12-05
forum: General Help
---

### Post by kartal on 2008-12-05
Hi

My ubuntu on my macbook pro was working fine last night. I think I used "suspend" to turn off my macbook pro. ANyways this morning when tried to wake it up, it did not want to. It gave some errors and did not go further. I thought that it needed a fresh start. So i did restart the laptop. Now all I have is 

"Grub _" 

on the screen and it does not go further.

I have 
-Macos installed
-One empty Ntfs partion (waiting to install xp)
-One Ubuntu installation

on my machine.

How can I fix it? I tried searching for a solution I have found that grub needs to be reinstalled. But in that example it is not clear where to install(since I have 3 partitions). I want to get further opinions before messiong up with what I have. And to be honest if I loose Ubuntu and need a fresh reinstall I prefer to install Xp and just give up on it for now. Since I have started using Ubuntu I lost so much time on setups, crashes and figuring things out, I am kind of out of free time to spend on it. I am really hoping that I would not need a fresh Ubuntu install.


Here is the suggested solution


"I think it's worth trying to repair Grub with the live CD, not supergrub. Here's the procedure. Boot up with the live CD and open a terminal. Now do:

sudo grubYou get the grub prompt, which is 'grub >'. Now do these three commands one after the other:

root (hd0,1)
setup (hd0)
quitand you are returned to the bash prompt. What that did is to re-install grub stage 1 to the mbr and grub stage 1.5 to the otherwise unused part of the HD immediately after the mbr, redirecting grub to stage 2 in /boot/grub in sda2 - your root partition. And yes, (hd0,1) and (hd0) is correct - grub has a different partition numbering convention.
"

---

### Post by caljohnsmith on 2008-12-05
OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo fsck -y /dev/sdXY
```
And please post the output. It might be doing an fsck on the partition is all you need, but we can work from there if not.

---

### Post by kartal on 2008-12-05
caljohnsmith, 

Thanks for the offer. Eventually I needed to get things asap.  I found a site that was explaning everything about grub in detail. And I found a way to reinstall grub on a partition (which is what I needed). The one I listed here was just going to install on default drive I assume.  I am glad that I did not go ahaed with it since my macbook has 3 different partitions with 3 different os setup.

After some mingling I managed to find out which parameters needed to reinstall grub. I ended up using these

root (hd0,3)
setup (hd0,3)

This one seemed to work 


thanks

---

