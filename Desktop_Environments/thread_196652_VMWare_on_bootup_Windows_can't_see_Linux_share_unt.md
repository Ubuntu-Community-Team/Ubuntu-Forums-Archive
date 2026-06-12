---
title: "VMWare: on bootup Windows can't see Linux share until I restart Samba"
date: 2006-06-14
forum: Desktop Environments
---

### Post by temcat on 2006-06-14
OK, so I gave up on setting up Windows share with authentication and set up shared folders on Linux (together with Subversion repository for my work files to have full-speed access to them in Windows). However, after I start Windows virtual machine, I can't access Linux shares until I restart Samba. Why is that? 

I must say I'm getting increasingly frustrated with Samba :-(

---

### Post by temcat on 2006-06-15
Bump :(

---

### Post by shanepardue on 2006-10-18
ever figure this out? because that is my issue..except mine isn't just windows. any computer on the network can't see my shares until i restart samba.

---

### Post by misha680 on 2006-10-19
I have actually had this issue for a while (ever since I started using VMWare server), I just thought it was something weird about VMWare and never really tried to figure it out, but maybe one of these days I'll have to look into it...

Misha

---

### Post by shanepardue on 2006-10-19
this happens with me on a regular network though. i know my issue isn't vmware. maybe our issues are different.

---

### Post by temcat on 2006-10-21
So it looks like it is indeed a Samba problem. And annoying one, too. I actually reverted to dual-booting some time ago being fed up with Samba troubles (the need to restart, inability to set up a proper multi-user authentication to Windows).

---

### Post by shanepardue on 2006-10-21
i'm sure there is an easy fix to this problem, but i don't know it! ha

---

### Post by airtonix on 2006-10-21
can you give us more details.....coz i haven't had those problems.....i setup samba *after* i installed vmware as per the howto forge guide at [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server) 

hat guide works perfect for me every time on a fresh dapper install

eit ; sorry misleading sentence ..... the guide doesnt talk about installing samba before or after or at all.....its just thats what i did....

Incidentally, vmware supports drag and drop between real session and virtual sesion

---

### Post by shanepardue on 2006-10-21
i decided to ditch samba anyway. ssh is a way more convenient/secure method of sharing files.

---

### Post by airtonix on 2006-10-21
damn right....microsoft still havent got the idea yet have they...sigh would be so damn simple to include an ssh implementation.....but noooooo.

they obvioulsy want the're clients to be as unsecure as possible

---

### Post by misha680 on 2006-10-21
Are you using network address translation or bridged networking? I am using NAT and have this problem (but it's not a big deal, after I boot up my virtual machine I just do a 
```
sudo /etc/init.d/samba restart
```
before accessing my shares and then everything is fine.

Misha

> **airtonix said:**
> can you give us more details.....coz i haven't had those problems.....i setup samba *after* i installed vmware as per the howto forge guide at [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server) 

hat guide works perfect for me every time on a fresh dapper install

eit ; sorry misleading sentence ..... the guide doesnt talk about installing samba before or after or at all.....its just thats what i did....

Incidentally, vmware supports drag and drop between real session and virtual sesion

---

### Post by gaumann on 2007-01-03
I am having this problem too. Restarting samba manually and everything works fine. I am using host only networking (vmnet1) on Edgy with vmware workstation. As far as I can tell the problem is caused by starting networking, samba and vmware services in the wrong order at bootup. If you look in the samba log files (in /var/log/samba) you can see lots of error messages about this. Samba is starting before the vmware service so the vmnet interfaces don't exist when samba starts and it ignores any references to them in its configuration. But when you restart the samba service manually the vmware service has already started and so the vmnet interfaces already exist and everything works fine. 

There is a solution here [http://ubuntuforums.org/showthread.php?t=201075&highlight=vmware+samba](http://ubuntuforums.org/showthread.php?t=201075&highlight=vmware+samba) but it is a bit of a hack.

---

### Post by gaumann on 2007-01-03
removing the line ```
bind interfaces only = yes
``` from /etc/samba/smb.conf fixed the problem for me.

---

### Post by sergio.callegari on 2007-01-18
Well... this is not really an option as it may well create security issues to some...

if you are using samba only to serve shares to vmware, you really want samba to bind only on the vmnet1 interface...

---

