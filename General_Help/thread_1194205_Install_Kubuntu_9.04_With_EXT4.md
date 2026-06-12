---
title: "Install Kubuntu 9.04 With EXT4"
date: 2009-06-22
forum: General Help
---

### Post by izizzle on 2009-06-22
Ok so after using kubuntu for a while with wubi, I finally decided to do the real install. I am a total noob at partitioning and I was wondering if someone could guide me through the install process. I want to install it with EXT4.

Thanks.

---

### Post by hyperdude111 on 2009-06-22
Don't worry about partitioning, its simple when you get used to it. 

Its a pretty easy process.

1. Download then burn Kubuntu or ubuntu .iso

2. Boot from cd by changing boot order in bios.

3. Run the installer from the cd.

4. Follow the instructions on the screen until you reach the partitioning screen.

6. Reduce size of your windows partition to create enough free space for ubuntu or if you want to remove windows delete its partition. 

7. In the space you have made create a new partition one 2gb for swap and another in the remaining space. This will be your .buntu partition format it to ext4, make the mountpoint "/".

8. Install Kubuntu to that partition and follow the rest of the instructions.

---

### Post by hibliss on 2009-06-22
> **hyperdude111 said:**
> 
7. In the space you have made create a new partition one 2gb for swap and another in the remaining space. This will be your .buntu partition format it to ext4, make the mountpoint "/".


The swap partition is like a pagefile in Windows. It is recommended to make it 1.5x your physical ram, so if you have 1gb of RAM, the swap should be 1.5gb (at least that is what I thought). Generic 2gb size seems strange.

There is an article here about linux swap file setup - [http://linux.com/news/software/applications/8208-all-about-linux-swap-space]("http://linux.com/news/software/applications/8208-all-about-linux-swap-space")

---

### Post by izizzle on 2009-06-22
Alright I have a question about the swap partition.

Type: Primary or Logical?
Location: Beginning or End?

Once I have everything figured out, I should have two partitions.

One as my main partition with the mount point set as "/".
Another With the swap.

Correct?

Thanks.

---

### Post by lovinglinux on 2009-06-22
These will certainly help

[https://help.ubuntu.com/9.04/installation-guide/i386/index.html](https://help.ubuntu.com/9.04/installation-guide/i386/index.html)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I would recommend [creating a separate partition for home](http://www.psychocats.net/ubuntu/separatehome), which is where you personal and configuration files will be stored, because it will save you a lot of trouble if you decide to downgrade, re-install or install a new release.

Keep in mind that if you choose ext4 you won't be able to install previous versions of Ubuntu without formatting the partition, in case you decide to change releases.

---

### Post by lovinglinux on 2009-06-22
> **izizzle said:**
> Alright I have a question about the swap partition.

Type: Primary or Logical?
Location: Beginning or End?

IMO, is better to put the swap in the beginning, because it is the fastest place of the disk. I don't remember, but I think swap doesn't let you choose if it is primary or logical. Besides, it would be a waste of primary partition, since you can have only 4 of them.

> **izizzle said:**
> 

Once I have everything figured out, I should have two partitions.

One as my main partition with the mount point set as "/".
Another With the swap.

Correct?

Correct, but as I said in the previous post, I also recommend creating a partition for home.

Create them in this order:

swap
root (/)
home

If you want to learn more how the position of the partitions could affect performance [read this](http://ubuntuforums.org/showpost.php?p=7391830&postcount=5).

---

### Post by izizzle on 2009-06-22
Thanks for the reply Loving. I have 150 GB to use. I allocated 2 GB to the swap. How much should I allocate to root (/) and how much to home?

Also, I take it that I should set swap as a logical partition then?

Thanks.

---

### Post by lovinglinux on 2009-06-22
> **izizzle said:**
> Also, I take it that I should set swap as a logical partition then?

I guess it doesn't matter. I think when you select swap you can set is as primary or logical. Swap is a different partition.

> **izizzle said:**
> Thanks for the reply Loving. I have 150 GB to use. I allocated 2 GB to the swap. How much should I allocate to root (/) and how much to home?

The size of the swap is OK. It should be 1.5 x your RAM size.

For home I would set something between 10 Gb and 20 Gb. Ubuntu by itself does not take much space, but if you want to install several large games for Linux (not Wine), then you might need more space. For example, I have a 20Gb root and I'm currently using only 5.9 Gb.

The home partition should take the rest, unless you want another partition for backups or data storage. If you like to storage lots of videos, then I would recommend creating one big partition for video storage at the end of the partition table.

---

### Post by izizzle on 2009-06-22
Alright so how does this sound:

Swap = 2GB
Root(/)= 17GB
Home = 130GB

I'm starting to think if I really need a HOME partition....does it really provide any benefits?

Thanks.

---

### Post by lovinglinux on 2009-06-22
> **izizzle said:**
> Alright so how does this sound:

Swap = 2GB
Root(/)= 17GB
Home = 130GB

It looks good, but there is an additional 1Gb missing. So set root as 18 Gb.

> **izizzle said:**
> I'm starting to think if I really need a HOME partition....does it really provide any benefits?

Oh yes. Trust me :)

For example, let's say you have a power failure and the root partition becomes irrecoverably corrupted ([ext4 can cause this](http://ubuntuforums.org/showthread.php?t=1133719)). Then you would have to re-install Ubuntu and would loose all your personal files. But if you have a separate home partition, all you have to do is re-install Ubuntu in the root partition and just [mount](http://www.psychocats.net/ubuntu/mountlinux) the home partition. Most of your configurations and all your personal files will be preserved, because they are stored on another partition.

Another example of the benefits of a separate partition is related to upgrades. I prefer to install a new Ubuntu release from fresh instead of upgrading, because there are several threads about issues after upgrades. So, when a new release is available, I just install it from fresh over my root partition, preserving the home, so all my settings (desktop, menus, themes, software preferences etc) are preserved, along with my personal files. So when I finish the installation process, my desktop looks exactly the same as before.

Another useful tip is that you can create a list of installed softwares, so when you install a new release you can download and install them all at once. You can do that with your current installation. Follow this:

> **lovinglinux said:**
> 
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```

This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository

---

### Post by izizzle on 2009-06-22
Thanks for the help lovinglinux, I'm definately sticking with what you have advised. Oh, and I actually have 149 GB not 150 GB, so root is still 17 GB. I'm probably gonna install later this week because I plan to get a new motherboard and would rather install once it is put in. 

I'll post back with the results!

---

### Post by lovinglinux on 2009-06-22
> **izizzle said:**
> Thanks for the help lovinglinux, I'm definately sticking with what you have advised. Oh, and I actually have 149 GB not 150 GB, so root is still 17 GB. I'm probably gonna install later this week because I plan to get a new motherboard and would rather install once it is put in. 

I'll post back with the results!

Good luck.

---

### Post by izizzle on 2009-07-01
I finally got it installed and it's working great!

Thanks for all the help!

---

