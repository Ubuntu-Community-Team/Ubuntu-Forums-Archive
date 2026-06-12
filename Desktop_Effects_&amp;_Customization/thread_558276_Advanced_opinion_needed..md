---
title: "Advanced opinion needed."
date: 2007-09-23
forum: Desktop Effects &amp; Customization
---

### Post by Wiebelhaus on 2007-09-23
What do you think or do you see any possible negative effects from these "tweaks" found [here]("http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed"):


> You want your Ubuntu desktop to be more responsive? It will take less than a half hour to perform all these tweaks. These tweaks will make your system faster and more responsive without a doubt. Read on to perform the tweaks and enjoy your faster system.

From what I understand these tweaks will work with all forms of Linux. They are not Ubunut Specific. I have only tried them on Ubuntu though, so if you use them on other Linux Distro's you do at your own risk.
Speed up your File System
About

Ubuntu Linux, unless you have set it up otherwise, uses the EXT3 system by default. It's a pretty good system. There are 3 journaling methods for EXT3 system.

    * Journal Data Writeback
    * Journal Data Ordered
    * Journal Data 

By default Ubuntu chooses "journal data ordered". In data=ordered mode, ext3 only officially journals metadata, but it logically groups metadata and data blocks into a single unit called a transaction. When it's time to write the new metadata out to disk, the associated data blocks are written first. data=ordered mode effectively solves the corruption problem found in data=writeback mode and most other journaled filesystems, and it does so without requiring full data journaling. In general, data=ordered ext3 filesystems perform slightly slower than data=writeback filesystems, but significantly faster than their full data journaling counterparts.

To speed it up, we are going to change it to the data=writeback system.
Tweak

    * Open your Grub boot menu. 

sudo nano -w /boot/grub/menu.lst

    * Look for the Defoptions and Altoptions and make them look like the entry below. 

# defoptions=quiet splash rootflags=data=writeback
# altoptions=(recovery mode) single rootflags=data=writeback

    * You need to update your Grub since you have altered it. 

sudo update-grub

    * Now we are going to edit the Fstab because it will be expecting these options. 

sudo nano -w /etc/fstab

    * Now you are going to want to add the (data=writeback and noatime=0) flags to your hard drive. It might be a little confusing because of the new naming system. Look for the (,errors=remount-ro) and add it afterwards to make it look like our example. 

defaults,errors=remount-ro,data=writeback,noatime 0

    * Now you tell your system to use them both. 

sudo tune2fs -o journal_data_writeback /dev/yourdrive

And you're done.


Concurrent Booting
About

Concurrent booting allows Ubuntu to take advantage of dual-core processors, as well as processors that hyperthread or multithread or what ever the different companies call it now.
Tweak

    * These settings are located in your /etc/init.d/rc file. Lets open it up. 

sudo gedit /etc/init.d/rc

    * Look through the file and you will find CONCURRENCY=none. You want to change it to: 

CONCURRENCY=shell

And you're done.


Swapping
About

Swappiness takes a value between 0 and 100 to change the balance between swapping applications and freeing cache. At 100, the kernel will always prefer to find inactive pages and swap them out; in other cases, whether a swapout occurs depends on how much application memory is in use and how poorly the cache is doing at finding and releasing inactive items.

The default swappiness is 60. A value of 0 gives something close to the old behavior where applications that wanted memory could shrink the cache to a tiny fraction of RAM. For laptops which would prefer to let their disk spin down, a value of 20 or less is recommended.
Tweak

    * First we have to gain access to your /etc/sysctl.conf file. 

sudo gedit /etc/sysctl.conf

    * Just scroll to the bottom of the page and add the tag listed below. The number you want depends on how much ram you have and what you do with your system. Please read the about above this to make your decision. I have mine set to 0 on a dual core laptop with 1 gig of ram and have seen no issues and a good performance gain. 

vm.swappiness=0

And you're done.


Broadband Internet
About

These are various tweaks taken from various places. Here is an article that explains them all if you would like to read it in depth. [http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html)
Tweak

    * You have to open your /etc/sysctl.conf file back up again. 

sudo gedit /etc/sysctl.conf

    * Then again, scroll to the bottom and just add these lines to it. 

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

    * You have to reset your sysctl for these to take effect. 

sudo sysctl -p

And you're done.


IPv6
About

IPv6 is an internet protocol. Most of your software uses IPv4 though and it causes conflicts.
Tweak

    * We are going to create a file. Paste this into a terminal. 

sudo gedit /etc/modprobe.d/bad_list

    * Then paste this into the file and save and exit the file. 

alias net-pf-10 off

And you're done.


Boot Profile
About

You have just made a lot of changes to your system. Re profiling your boot will reorganize it and make it faster on boots afterwards.
Tweak

    * Reboot your PC.
    * When you come to your grub list, hit escape to see your grub menu.
    * Edit the topmost line and add the word below to the end of it. 

profile

    * Then just reboot the system. 


Now you are done and you can enjoy your faster Ubuntu System.






---

### Post by Wiebelhaus on 2007-09-23
I said to hell with it and tried it , After only about ten minutes I can honestly say it has greatly improved the performance on this system , only time will tell - But this may become part of my default setup procedure.

---

### Post by Izobalax on 2007-09-23
Bookmarked! Love it!

/izo

---

