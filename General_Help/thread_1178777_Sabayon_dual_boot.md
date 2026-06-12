---
title: "Sabayon dual boot"
date: 2009-06-04
forum: General Help
---

### Post by logicalform on 2009-06-04
Hey guys,
I've been distro shopping recently and I've come down to Linux Mint and Sabayon. I love Sabayon, but it's a bit more difficult than the *buntus, so I thought I'd install it alongside Mint to cover my bases. I'll play with Sabayon to learn more about compiling and whatnot and keep Mint for when I just need stuff to work (and so my girlfriend can figure stuff out...) Anyway, being a noob, I need some help regarding the installation, partition schemes, etc. Here are my basic questions, but please feel free to offer any advice you can think of:

1) Can you offer an example partition scheme for sharing two distros on one HD?
2) Can two distros share the same swap partition?
3) Setting up the bootloader?
4) Any advice on how to shrink my current Mint partition to make room for the new one (without destroying everything) - GParted wouldn't let me alter my Mint partition as it was in use. Will I just have to wipe it clean?

Sorry to be long-winded - I'm a noob, but I've been so impressed with Linux and the whole communal aspect of the open source community that I can't imagine ever going back, so I really want to become proficient at this whole thing.

Thanks in advance for any and all help anyone can give me.

---

### Post by Soul-Sing on 2009-06-04
2) yes
3)+4) install ubuntu [COLOR="Red"]after[/COLOR] installing sabayon or whatever.
ubuntu delivers your GRUB en makes a partition next to other distro's
4) or take the gparted iso, burn it and use this live cd to partition/organize your sytem.

---

### Post by Soul-Sing on 2009-06-04
1)

---

### Post by gamblor01 on 2009-06-04
> **logicalform said:**
> 
1) Can you offer an example partition scheme for sharing two distros on one HD?
2) Can two distros share the same swap partition?
3) Setting up the bootloader?
4) Any advice on how to shrink my current Mint partition to make room for the new one (without destroying everything) - GParted wouldn't let me alter my Mint partition as it was in use. Will I just have to wipe it clean?


1) This is up to you.  It really depends on how much space you want for each OS.

2) As mentioned before, yes.  So can 3, 4, or any other number of distros.

3) You don't need to reinstall Mint after installing Sabayon to accomplish this (though it's the easiest way).

Grub looks at the file /boot/grub/menu.lst in order to find out what partitions are available for it to boot.  You have a few other options besides reinstalling:

-- Install Sabayon with *NO* bootloader.  Then manually configure the menu.lst file to point the the appropriate partition and the kernel and initrd that reside there.
-- Install Sabayon with a bootloader *ON THE SABAYON PARTITION* and then configure the menu.lst file on Mint to chainload the Sabayon partition.  This basically means that grub is installed on both partitions and instead of trying to boot the partition, Mint hands control over to the Sabayon partition (which has it's own menu.lst file) and it boots itself.

4) As previously suggested, your best bet is to use the gparted live CD.  This way the partition isn't mounted while you're trying to change it.


During step 3, it's possible that you accidentally install the Sabayon bootloader to the MBR, also known as (hd0).  If so there is nothing to worry about -- you can always reinstall the grub for Mint (or just configure Sabayon's menu.lst file to boot/chainload Mint).

If you want to give us some better info to start with, you might want to paste the output of

```

sudo fdisk -l

```

---

### Post by logicalform on 2009-06-05
Thanks for the replies, guys. Here's the output from fdisk:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29484   236830198+  83  Linux
/dev/sda2           29485       30401     7365802+   5  Extended
/dev/sda5           29485       30401     7365771   82  Linux swap / Solaris

Sorry if I've misunderstood anything, but does the following sound like an easy enough plan?

1) Make GParted live cd
2) Resize
3) Install Sabayon on the new partition
4) Reinstall Mint on its partition (this is the part I'm a little bit confused about)
5) Everything works? Or would I still need to do something with grub?

Also, I forgot one question in my original post. I think Sabayon 4.1 defaults to ext4 (although I could be wrong), while Mint uses ext3. If I were to create a separate partition for sharing media files between the distros, what format should it be? Would the two OS partitions have to be the same in order to write to the media partition?

Thanks for your time helping me to learn. I look forward to one day being on the other side of this discussion, haha.

---

### Post by gamblor01 on 2009-06-05
[quote=logicalform]
Sorry if I've misunderstood anything, but does the following sound like an easy enough plan?
[/quote]
I would recommend the following:


1) Make GParted live cd
2) Resize the sda1 partition
3) Create a new partition (sda3)
4) Install Sabayon on the new partition (sda3)  -- see further suggestions below
5) Edit your /boot/grub/menu.lst file on /dev/sda1 (Mint's partition) to include a line for booting Sabayon.
6) Enjoy your dual boot setup!


There is no need to reinstall Mint if you just manually add lines to your menu.lst file.  To make this as simple as possible, I would suggest that during the Sabayon installation you select the option to install grub (bootloader) but MAKE SURE you install it to /dev/sda3, not (hd0), not sda...make sure it's /dev/sda3.  Then you can just edit the menu.lst file on Mint, and add on the following lines at the end:

```

title        Sabayon (on /dev/sda3)
root        (hd0,2)
chainloader    +1

```The title line can be anything (it's just what gets displayed in the grub menu) but the root line says to look on the partition (hd0,2) -- also known as dev/sda3.  Then chainloader just says to transfer control to the bootloader found on the defined root partition (so it transfers control to the Sabayon bootloader, which if you properly followed my instructions above, is installed on /dev/sda3).

If you ask me, it's much less effort to click the option to install grub on /dev/sda3 and then add the above 3 lines to your menu.lst file as opposed to completely reinstalling Mint!


Also, you should be able to change the default filesystem type to ext3 during the installation.  You don't really need any separate partition either because you can just mount one from the other (not sure if Mint can mount the ext4 partition, but if they are both ext3 it will work).

For example, if you're in Sabayon and you want the files from your Mint partition you can do something like:

```

mkdir /media/sda1
mount /dev/sda1 /media/sda1

```Now the files for your Mint install are available to you in /media/sda1 so type in
```

cd /media/sda1

```and you'll see them all.

---

### Post by logicalform on 2009-06-06
Wow, thanks for the detail. I think I have a plan of action now, and I've learned some things to boot (har har). Hopefully I'll get some time to do this all this weekend and enjoy my new setup. BTW, how is Mint/Ubuntu with ext4? Too buggy?

---

### Post by randiroo76073 on 2009-06-06
I'm running Ubuntu 9.04 on my test machine w/ext4 and haven't had any probs yet. Been using it since alpha 2-3 I think :) My Main machine has 7 distros on it and I use chainloaders, works best for me :)

---

