---
title: "Mounting NFS shared VERY slow"
date: 2006-07-16
forum: Desktop Environments
---

### Post by leupi on 2006-07-16
A while back I installed Kubuntu 5.10 and had an issue with mounting NFS shares that resided on a FC3 server. It took over two minutes to mount the share; once it was mounted everything was fine but the initial wait was a bit silly. My SuSE boxes mounted it within seconds. I added a line to my fstab file to automount and that made the bootup time on the computer VERY slow.

I now have Kubuntu 6.06 on two seperate computers and I am having the same issue on both. The SuSE boxes still mount it fine. I have entries in my /etc/hosts file, I tried mounting using both the computer name and the IP address. I love Kubuntu but this is a bit frustrating. Any ideas? Thanks.

Todd

---

### Post by llbbl on 2006-07-28
It mounts for me really slow also. I don't know how to fix it .... /cry

---

### Post by fluffnik on 2006-07-28
> **leupi said:**
> A while back I installed Kubuntu 5.10 and had an issue with mounting NFS shares that resided on a FC3 server. It took over two minutes to mount the share; once it was mounted everything was fine but the initial wait was a bit silly. My SuSE boxes mounted it within seconds. I added a line to my fstab file to automount and that made the bootup time on the computer VERY slow.

Similar here; 2TB raid and a scratchspace exported to my whole network mounts near instantly to an assortment of Debian [sid,sarge] and Mepis 3.4-3 machines, takes an age with Ubuntu...

> **leupi said:**
> 
I now have Kubuntu 6.06 on two seperate computers and I am having the same issue on both. The SuSE boxes still mount it fine. I have entries in my /etc/hosts file, I tried mounting using both the computer name and the IP address. I love Kubuntu but this is a bit frustrating. Any ideas? Thanks.

Since all my Ubuntu machines are laptops - single user - I've put "users,noauto" in fstab and mount via a script in Gnome's session startup.

The scrip is not really necessary AFAIK since the existance of (noauto) mountpoints in /etc/fstab seems to cause an entry in the "Places" menu which will mount (slowly) on demand.

---

### Post by roax on 2006-07-28
apt-get install portmap

---

### Post by fluffnik on 2006-07-29
> **roax said:**
> apt-get install portmap

Bingo!

I didn't expect nfs to work *at all* without the portmapper,  so  I never thought to check it was there...

---

### Post by leupi on 2006-08-12
That worked great! Thanks.

---

