---
title: "FN Key on Dell 1420N?"
date: 2007-09-13
forum: Dell  Ubuntu Support
---

### Post by cheuschober on 2007-09-13
Hi.

I have a new 1420N and did what every good little linux user does and wiped the harddrive and installed fresh on a more efficient partition scheme but I'm afraid I can't get my FN key to work. Is this a dell bios setting that needs to be adjusted or is there a specific kernel config or software handler?

Does anyone's FN key do its job?

Regards and thanks,
~c

---

### Post by notwen on 2007-09-13
I did not wipe my 1420n's HDD, as nothing like a very useful recovery install option via GRUB should something horrid happen and I am unable to get a hold of a new image to burn.  You could check the thread of other users who have wiped their 1420n's partition table and installed from scratch [here]("http://ubuntuforums.org/showthread.php?t=509408").  I don't recall any of the posts mentioning any issues w/ the Fn key, but maybe someone has posted since I last browsed through them all.  You may also want to try using one of the brand new Dell Feisty images just released [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Download_Dell_Ubuntu_Image").  I'm not sure if this implements the Fn Keys, but it should remedy the majority of the issues users doing a clean install of Feisty on the 1420n encounter(ie synaptic scrollpad, cd-rom not picking up, etc).  Please post back should any of this help you or if you come across a fix elsewhere.  Good luck.

---

### Post by cheuschober on 2007-09-13
Thanks for the info :). You're right, that probably would 'just work' but I'd like to at least know what the problem is in case I want to install and dual boot with other distros (studio64 comes to mind) in one of my empty partitions.

Maybe a better question would be to ask for someone with a working 1420N fn key to offer...

1) lspci -v
2) lsmod
3) cat /usr/src/linux/.config
4) dpkg -l

With those in place (I hope) I could be able to diff out what I'm missing.

Many thanks,
~C

---

### Post by kuja on 2007-09-13
> **cheuschober said:**
> Thanks for the info :). You're right, that probably would 'just work' but I'd like to at least know what the problem is in case I want to install and dual boot with other distros (studio64 comes to mind) in one of my empty partitions.

Maybe a better question would be to ask for someone with a working 1420N fn key to offer...

1) lspci -v
2) lsmod
3) cat /usr/src/linux/.config
4) dpkg -l

With those in place (I hope) I could be able to diff out what I'm missing.

Many thanks,
~C

Substituted /boot/config-`uname -r` for #3, but that should suffice really.

---

### Post by cheuschober on 2007-09-13
Kuja, you're  gem.

Thank you many times over.

---

