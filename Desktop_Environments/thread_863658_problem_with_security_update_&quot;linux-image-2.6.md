---
title: "problem with security update: &quot;linux-image-2.6.24-19-386&quot;"
date: 2008-07-18
forum: Desktop Environments
---

### Post by Zizo on 2008-07-18
I am trying to install the security update: linux-image-2.6.24-19-386. However, at the middle of the installation I get the following error: 

**E: /var/cache/apt/archives/linux-image-2.6.24-19-386_2.6.24-19.36_i386.deb: failed in buffer_write(fd) (10, ret=-1)**

any ideas for a solution?

Thank you in advance

---

### Post by warp99 on 2008-07-20
Delete this file:

```
sudo rm /var/cache/apt/archives/linux-image-2.6.24-19-386_2.6.24-19.36_i386.deb
```

then try the update again.

---

### Post by Zizo on 2008-07-23
Before reading your suggestion, I wanted to empty some space from the /boot partition. So I tried to remove some old kernel versions. I went to 'Synaptic Package Manager', I searched for 'linux-image-2' and tried to completely remove **'linux-image-2.6.24-16-386'**, the window mentioned that '**linux-image-2.6.24-17-386**' is to be removed too. I apply and get the following error message: [B]E: linux-ubuntu-modules-2.6.24-17-386: subprocess post-removal script returned error exit status 1

[/B]The second issue now is  when I try to install new updates I get the following message: **Not all updates can be installed**, **Run a partial upgrade, to install as many updates as possible**. 
I run the partial upgrade and I get the following message: [B]Not enough free disk space. The upgrade aborts now. The upgrade needs a total of 31.5M free space on disk '/boot'. Please free at least an additional 22.5M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
[/B]I have nothing in the trash and I removed temporary packages using sudo apt-get clean, but the problem persists.

What is going on in my system? I am using Ubuntu 8.04. Any ideas on how to solve the two above mentioned issues that I am having?

Thank you in advance

---

### Post by warp99 on 2008-07-23
> **Zizo said:**
> ... Not enough free disk space. The upgrade aborts now. The upgrade needs a total of 31.5M free space on disk '/boot'. Please free at least an additional 22.5M of disk space on '/boot'. 

You have a separate partition for your /boot directory and there is not enough drive space on that partition to complete the partial upgrade.

The best thing to do is boot to a Gparted LiveCD or LiveUSB shrinking another partition and growing your /boot partition. You can use a Ubuntu LiveCD/USB to do the same thing, but the Gparted version is much easier. You can get Gparted here:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Once you grow the partition for the additional space you should be able to complete the remaining operations. Just make sure its large enough for future updates.

---

### Post by Zizo on 2008-07-25
> **Zizo said:**
> Before reading your suggestion, I wanted to empty some space from the /boot partition. So I tried to remove some old kernel versions. I went to 'Synaptic Package Manager', I searched for 'linux-image-2' and tried to completely remove **'linux-image-2.6.24-16-386'**, the window mentioned that '**linux-image-2.6.24-17-386**' is to be removed too. I apply and get the following error message: **E: linux-ubuntu-modules-2.6.24-17-386: subprocess post-removal script returned error exit status 1**

I solved the problem by removing everything related to **linux-ubuntu-modules-2.6.24-17-386* **from  **/var/lib/dpkg/info** and then I issued the following commands:

sudo apt-get install -f
sudo apt-get update

and the problem was solved. Both,** linux-image-2.6.24-16-386** and **linux-image-2.6.24-17-386** were removed.


> **Zizo said:**
> 
The second issue now is  when I try to install new updates I get the following message: **Not all updates can be installed**, **Run a partial upgrade, to install as many updates as possible**. 
I run the partial upgrade and I get the following message: [B]Not enough free disk space. The upgrade aborts now. The upgrade needs a total of 31.5M free space on disk '/boot'. Please free at least an additional 22.5M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
[/B]I have nothing in the trash and I removed temporary packages using sudo apt-get clean, but the problem persists.

After removing the above kernel versions I got more space in /boot and I was able to install new updates.

---

### Post by warp99 on 2008-07-26
> **Zizo said:**
>  After removing the above kernel versions I got more space in /boot and I was able to install new updates.

I would still grow the partition on /boot so you won't run into this problem in the future.

---

