---
title: "sys won't boot from menu, Install Disk, nor a Super Grub Disk"
date: 2013-02-23
forum: Desktop Environments
---

### Post by confused1 on 2013-02-23
Hi folks I could use some help
Ubuntu version that was in use was latest before 12 

I have been using a dual boot configuration with Win7 and Ubuntu flawlessly for a couple of years and now due to an update or whatever, I can only boot into Win7 from the menu screen. I have tried using an Ubuntu 11.04 Install Disk, but the only option that works is a boot into Win7. I tried using a Super Grub Disk that has worked in the past but does not work now.
When I boot from the Hard Drive menu, the Ubuntu Install DIsk, or the Super Grub Disk I usually end up with the following message:

udevadm settle- timeout of 120 seconds reached, the event queue contains: /sys/devices/pci0000:00/oooo:02.0(983)  
or
/sys/devices/pci0000:00/0000:1c.7/0000:08:00.0(1007) 

Gave up waiting for root device
Boot args (cat/proc/cmdline
check root delay
check root
mising modules (cat/proc/modules; ls/dev
Fatal could not load /lib/modules


Much thanks in advance- hope its something simple

---

### Post by oldfred on 2013-02-23
Are you still using 11.04, if not best to use LiveCD/DVD/Flash that is same version.

If stil using 11.04 it is time to upgrade to 12.04 or newer as 11.04 is out of support.

I do not know error but might try fsck first.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by confused1 on 2013-02-23
Solved
Thanks oldfred - I went ahead and downloaded the latest 12.10 ver ISO to a thumb drive and installed from there- no problems so far
It still seems like my old version should have booted even though it was outdated-  just scratching my head.

Thanks again

---

