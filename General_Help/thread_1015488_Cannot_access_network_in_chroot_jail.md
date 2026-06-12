---
title: "Cannot access network in chroot jail"
date: 2008-12-18
forum: General Help
---

### Post by tianran.chen on 2008-12-18
Greetings,

I am trying to install a Gentoo linux inside a Ubuntu 8.10 chroot jail for software development purpose. However, I have trouble accessing the network once I'm inside the chroot jail. And it seems to be a permission issue. Here's what I did:

```

xxx@oolong:~/dev/mini$ cp -L /etc/resolv.conf gentoo/etc/
xxx@oolong:~/dev/mini$ cp -L /etc/hosts gentoo/etc/
xxx@oolong:~/dev/mini$ sudo mount -t proc none gentoo/proc
xxx@oolong:~/dev/mini$ sudo mount -o bind /dev gentoo/dev
xxx@oolong:~/dev/mini$ sudo chroot gentoo /bin/bash
oolong / # env-update
>>> Regenerating /etc/ld.so.cache...
oolong / # source /etc/profile
oolong / # ping www.google.com
**ping: icmp open socket: Operation not permitted**
oolong / # ifconfig eth1
eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fee7:13ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1304303 (1.2 Mb)  TX bytes:212621 (207.6 Kb)
          Interrupt:251 Base address:0xc000 

```

ping cannot even open a socket, so this looks to be not a resolv.conf problem. After some searching, I run into this kernel.grsecurity.chroot_caps option which is supposedly located inside /proc, however, I cannot find it. Any ideas? Thanks in advance.

---

### Post by caljohnsmith on 2008-12-18
How about also binding the following directories before you chroot:
```
sudo mount --bind /tmp gentoo/tmp
sudo mount --bind /sys gentoo/sys
```
It may not seem like you need to bind /tmp to the chroot jail, but if you want to run any GUI apps for instance, it is a must. I read somewhere that it is necessary when the kernel creates a new socket, so I think that might apply to you. How about giving it a shot and let me know if it makes any difference.

---

### Post by tianran.chen on 2008-12-18
> **caljohnsmith said:**
> How about also binding the following directories before you chroot:
```
sudo mount --bind /tmp gentoo/tmp
sudo mount --bind /sys gentoo/sys
```
It may not seem like you need to bind /tmp to the chroot jail, but if you want to run any GUI apps for instance, it is a must. I read somewhere that it is necessary when the kernel creates a new socket, so I think that might apply to you. How about giving it a shot and let me know if it makes any difference.

Thanks. But still the same. Now both /tmp and /sys are visible inside chroot jail. But still no luck.

---

### Post by albinootje on 2008-12-18
> **tianran.chen said:**
> Thanks. But still the same. Now both /tmp and /sys are visible inside chroot jail. But still no luck.

I know it's a cruel solution perhaps, but why not install gentoo inside a VM with qemu or VirtualBox ?
If you only need a virtual console, then qemu might be a handy solution.

---

### Post by tianran.chen on 2008-12-18
> **albinootje said:**
> I know it's a cruel solution perhaps, but why not install gentoo inside a VM with qemu or VirtualBox ?
If you only need a virtual console, then qemu might be a handy solution.

One reason is that I want to be able to automatically build my software packages using portage system, and test it in a gentoo environment. Sure, VirtualBox would work, but it's going to be pretty slow, since I only have a Pentium4 which does not support any virtualization. And I have to rewrite the whole testing system.

Second reason is just that this should be doable. Isn't it how many network services are being executed?

P.S., I tried this in the server version as well, and same problem.

---

### Post by caljohnsmith on 2008-12-19
Just as a sanity check, can you ping Google OK while you are in Ubuntu (outside of the Gentoo chroot jail)?

---

### Post by albinootje on 2008-12-19
> **tianran.chen said:**
> One reason is that I want to be able to automatically build my software packages using portage system, and test it in a gentoo environment. Sure, VirtualBox would work, but it's going to be pretty slow, since I only have a Pentium4 which does not support any virtualization. And I have to rewrite the whole testing system.

Second reason is just that this should be doable. Isn't it how many network services are being executed?


You're right that it should be doable.

(That reminds me, I vaguely remember that some weeks ago i was testing some VPS with Ubuntu Intrepid, i stopped the VPS, and wanting to use chroot on it, and i got some error right away! I was surprised because I have been using chroot with Debian and Ubuntu  (and before with Slackware and RedHat) since years without problems.)

---

### Post by tianran.chen on 2008-12-19
> **caljohnsmith said:**
> Just as a sanity check, can you ping Google OK while you are in Ubuntu (outside of the Gentoo chroot jail)?

Well, yeah. Everything work just fine outside the chroot jail. And no network access at all inside the jail, not just ping.

---

### Post by tianran.chen on 2008-12-19
> **albinootje said:**
> You're right that it should be doable.

(That reminds me, I vaguely remember that some weeks ago i was testing some VPS with Ubuntu Intrepid, i stopped the VPS, and wanting to use chroot on it, and i got some error right away! I was surprised because I have been using chroot with Debian and Ubuntu  (and before with Slackware and RedHat) since years without problems.)

I wrote the testing system, which uses chroot jail, for Arch Linux originally and it still work now.

...I wonder if anyone can confirm this result.

---

### Post by caljohnsmith on 2008-12-19
It sounds to me like maybe you simply don't have all the required packages necessary to have internet access installed yet in Gentoo? You might have to download the packages in Ubuntu and then move them into Gentoo. Does Gentoo have a website similar to packages.ubuntu.com where you can download individual packages?

---

### Post by tianran.chen on 2008-12-19
> **caljohnsmith said:**
> It sounds to me like maybe you simply don't have all the required packages necessary to have internet access installed yet in Gentoo? You might have to download the packages in Ubuntu and then move them into Gentoo. Does Gentoo have a website similar to packages.ubuntu.com where you can download individual packages?

gentoo has "emerge" which is equivalent to "apt-get" in Ubuntu, and it also has [www.gentoo.org/packages](www.gentoo.org/packages). But I do think all the softwares are there already, since if I boot into my Arch Linux on the same machine, then I can choot to the Gentoo installation and access the network with no problem.

---

### Post by albinootje on 2008-12-19
> **tianran.chen said:**
> I wrote the testing system, which uses chroot jail, for Arch Linux originally and it still work now.

...I wonder if anyone can confirm this result.

I just did the following on a OpenVZ host (Debian) that i have :
1) I used a gentoo template to create a VPS
2) Brought the VPS with gentoo up, pinging worked
3) I shut down the VPS with gentoo
4) Did a chroot /vz/private/111 (dir with gentoo VPS)
5) Did a ping, it worked

To summarize, i didn't have to do anything *before* using the
chroot command to make this work.

I think (I downloaded it some months ago) the template is the 
gentoo-20060317-i686-stage3.tar.gz
from [http://wiki.openvz.org/Download/template/precreated](http://wiki.openvz.org/Download/template/precreated)

GL!

---

