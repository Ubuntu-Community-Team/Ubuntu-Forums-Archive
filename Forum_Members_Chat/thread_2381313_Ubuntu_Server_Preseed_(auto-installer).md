---
title: "Ubuntu Server Preseed (auto-installer)"
date: 2017-12-29
forum: Forum Members Chat
---

### Post by LHammonds on 2017-12-29
I have noticed there is very little documentation and working examples about preseeding and much of what is out there is incorrect or no longer applicable to the current versions.

I've started trying to learn this process and once I have a firm understanding of it, I'll post another tutorial on how others can do the same.

The servers I setup tend to have a lengthy install process...mainly about configuring LVM and partitions.  Preseeding will make the install extremely fast to make a production-level server.

However, I do realize that a preseed scenario of for a very small niche of users. ;)

In the past, I have always just setup a template server how I like to roll them out and let VMware deploy the images.  But I'm curious on how to do this in a more generic framework that will work anywhere (vmware, virtualbox, bare metal, etc.)

LHammonds

---

### Post by Paddy Landau on 2017-12-30
Here is an area where I feel ignorant. What do you mean by "preseed"? (It sounds like "precede", which I suspect is a good pun in this context.)

---

### Post by LHammonds on 2018-01-01
> **Paddy Landau said:**
> Here is an area where I feel ignorant. What do you mean by "preseed"? (It sounds like "precede", which I suspect is a good pun in this context.)
Don't feel bad about being ignorant about it.  I have been using Ubuntu Server since 10.04 and have not messed with it until now so I'm right there with you in the ignorance boat.

Pre-seeding is just pre-answering questions the installer asks.

The distributions already do this and how they pre-configure various scenarios.

My goal is to configure an ISO image that will automatically answer all the install questions without any interaction so that when I power up the VM, I walk away and come back a few minutes later to a login prompt ready for me to being setting it up for the specific purpose I need it for...rather than messing about trying to get it ready to be one of my standard "base" servers.  I just want it to roll out that way.

Here are some reference links about the subject.

[Appendix B. Automating the installation using preseeding]("https://help.ubuntu.com/lts/installation-guide/amd64/apb.html")
 
[Preseed Example]("https://help.ubuntu.com/lts/installation-guide/example-preseed.txt")

[AskUbuntu.com Question that was self-answered]("https://askubuntu.com/questions/806820/how-do-i-create-a-completely-unattended-install-of-ubuntu-desktop-16-04-1-lts")

LHammonds

---

### Post by Paddy Landau on 2018-01-01
> **LHammonds said:**
> Pre-seeding is just pre-answering questions the installer asks.
Thanks, I understand now. Sorry that I don't know how to solve it.

---

### Post by LHammonds on 2018-01-02
> **Paddy Landau said:**
> Thanks, I understand now. Sorry that I don't know how to solve it.Not many do (or have it documented with 16.04) which is part of why I'm interested in it.

I'll get it figured out.  It takes quite a while to make a change, re-compile, boot, wait for problem, repeat cycle.  Lots of trial-n-error.

LHammonds

---

### Post by deadflowr on 2018-01-02
This (And these if you look through the forks) give you some ideas on setting up preseed for lvms?
[https://gist.github.com/lorin/5140029]("https://gist.github.com/lorin/5140029")

---

### Post by LHammonds on 2018-01-04
> **deadflowr said:**
> This (And these if you look through the forks) give you some ideas on setting up preseed for lvms?
[https://gist.github.com/lorin/5140029](https://gist.github.com/lorin/5140029)
That is a somewhat working partition pre-seed but it is very-much like all the others out there.  It is basically the "atomic" configuration where most everything is on one partition.  When I start breaking it out into multiple partitions, it always breaks and I have determined the root cause is the size assignment values (the 3 numbers).

I found [this article]("https://www.bishnet.net/tim/blog/2015/01/29/understanding-partman-autoexpert_recipe/") that explains how the 3 numbers are supposed to work but even knowing that, I still cannot get it working yet.  It bombs out if I specify a root partition of a lower value than max.  I have not found out the exact specifics yet as it takes quite a while to test each time I make a small change.  It might also be that partman requires/expects a lot larger hard drive space.  The example you linked assumed a 256GB root partition with everything going to the data partition.  With my 30GB drive, it couldn't fit the tmp and data so it only had the boot and root partitions.

When I partition manually, I can set each partition to no more than 2GB and everything fits just fine but partman blows chunks when I try to partition it the same way I do it manually.

Example of the recipe I am trying to make (with a 30GB hard drive):
```

d-i partman-auto/expert_recipe string prod-server :: \
  500 500 500 ext2 \
    $primary{ } \
    $bootable{ } \
    $lvmignore{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext2 } \
    mountpoint{ /boot } \
    label{ boot } \
  .\
  120% 2048 120% linux-swap \
    $lvmok{ } \
    format{ } \
    in_vg{ LVG } \
    lv_name{ swap } \
    method{ swap } \
  .\
  2000 2000 2000 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ root } \
    mountpoint{ / } \
    label{ root } \
  .\
  200 200 200 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ home } \
    mountpoint{ /home } \
    label{ home } \
  .\
  500 500 500 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ tmp } \
    mountpoint{ /tmp } \
    label{ tmp } \
    options/relatime{ relatime } \
    options/noexec{ noexec } \
    options/rw{ rw } \
  .\
  2000 2000 2000 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ usr } \
    mountpoint{ /usr } \
    label{ usr } \
  .\
  2000 2000 2000 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ var } \
    mountpoint{ /var } \
    label{ var } \
  .\
  200 200 200 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ srv } \
    mountpoint{ /srv } \
    label{ srv } \
  .\
  200 200 200 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ opt } \
    mountpoint{ /opt } \
    label{ opt } \
  .\
  500 500 500 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ bak } \
    mountpoint{ /bak } \
    label{ bak } \
  .\

```

---

### Post by Paddy Landau on 2018-01-05
Ubuntu Server requires at least 25Gb disk space. Once you start to partition it into smaller blocks, it will be problematic, which may explain your difficulties on a 30Gb drive (which is tiny by today's standards).

For a 30Gb drive, I would recommend just a single partition. Not even a Swap partition; use a file-based swap instead.

---

### Post by LHammonds on 2018-01-05
> **Paddy Landau said:**
> Ubuntu Server requires at least 25Gb disk space. Once you start to partition it into smaller blocks, it will be problematic, which may explain your difficulties on a 30Gb drive (which is tiny by today's standards).

For a 30Gb drive, I would recommend just a single partition. Not even a Swap partition; use a file-based swap instead.

Actually, you can easily install Ubuntu Server 16.04 LTS onto a 10GB drive.   Here is a default install with Guided-LVM selected and OpenSSH enabled:

```

root@ubuntu:/# vgdisplay
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               9.52 GiB
  PE Size               4.00 MiB
  Total PE              2437
  Alloc PE / Size       2431 / 9.50 GiB
  Free  PE / Size       6 / 24.00 MiB
  VG UUID               h53Zon-9HIb-6qgT-lgKQ-JOSV-T3px-jldSMa

```
```

root@ubuntu:/# df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         477M     0  477M   0% /dev
tmpfs                        100M  3.2M   97M   4% /run
/dev/mapper/ubuntu--vg-root  8.3G  1.4G  6.5G  17% /
tmpfs                        497M     0  497M   0% /dev/shm
tmpfs                        5.0M     0  5.0M   0% /run/lock
tmpfs                        497M     0  497M   0% /sys/fs/cgroup
/dev/sda1                    472M   58M  391M  13% /boot
tmpfs                        100M     0  100M   0% /run/user/1000

```

EDIT:  The above is a clean install of 16.04.3.  The below is after doing the apt-get upgrade, dist-upgrade:

```
root@ubuntu:/# df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         477M     0  477M   0% /dev
tmpfs                        100M  3.2M   97M   4% /run
/dev/mapper/ubuntu--vg-root  8.3G  1.8G  6.1G  22% /
tmpfs                        497M     0  497M   0% /dev/shm
tmpfs                        5.0M     0  5.0M   0% /run/lock
tmpfs                        497M     0  497M   0% /sys/fs/cgroup
/dev/sda1                    472M  106M  342M  24% /boot
tmpfs                        100M     0  100M   0% /run/user/1000
root@ubuntu:/# uname -a
Linux ubuntu 4.4.0-104-generic #127-Ubuntu SMP Mon Dec 11 12:16:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```


The 30GB drive is more than enough room to create a base server with room to grow.  The point of my tutorials is to show how to design the partition system to grow and that also includes keeping it small...initially and then grow where needed.  To see this illustrated, you can look over these two sections in my how-to guide: [Analysis and Design]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220#p445"), [Volume and Disk Management]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220#p447")

As for file-based swap, I will address that in 18.04...most-likely with a fixed swap partition and how to add a swapfile on top of that if needed if not using SSD.  However, your server should be tuned so that it does not USE the swap partition.  Different story altogether for desktop systems though.

LHammonds

---

