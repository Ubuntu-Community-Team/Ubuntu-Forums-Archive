---
title: "NFS volume takes minutes to mount"
date: 2006-06-20
forum: Desktop Environments
---

### Post by grough on 2006-06-20
Hi,

I have two machines running Ubuntu 6.06, one of which is used primarily as storage and a home web server.

I am using NFS to access a 200GB drive on the storage machine from the client machine. It performs very well... with one exception: It takes somewhere between one and two minutes just to mount the NFS drive on the client machine. I've used NFS in similar setups before, but have never experienced any delay. It happens when mounting on boot, and manually.

The storage machine is running Ubuntu 6.06 Server AMD64
The client machine is running Ubuntu 6.06 Desktop i386

The entry in the client's fstab is:
192.168.1.100:/media/storage  /media/storage  nfs  defaults,rw  0 0

Is there any reason I should experience such a delay when mounting an NFS volume?

---

### Post by powerflex on 2006-07-11
Hi grough

I have absolutely the same problem.
My Server is Debian Sarge 3.1.
The Problem-Client is Ubuntu 6.06.
With two Debian Sarge Clients i have no Problems.

Do you have solved the problem?

---

### Post by grough on 2006-07-11
>Do you have solved the problem?

Sadly not. I'm using the server with windows+samba now, which works just fine (gave up on Ubuntu 6.06 after wireless/ndiswrapper stopped working).

---

### Post by Dubbayoo on 2006-07-11
I noticed that problem last week. Oddly it seemed that nfs-common was somehow removed from my system but my nfs drives would mount 20-30 minutes after bootup even though they are in fstab. I reinstalled nfs-common and that seemed to take care of it.

---

### Post by powerflex on 2006-07-12
I removed (it was installed) and reinstall the nfs-common package but the Problem is still there.

---

### Post by ensiferum on 2006-07-12
I had the same problem. Reading this thread I noticed the reference to nfs-common, which I didnt even have installed! Oddly though the mount would still succeed, just take forever.

Works fine now.

---

### Post by alalbiol on 2006-10-16
I think that the problem is that portmap is not installed 
by default in ubuntu, you can check this by typing dmesg 
after the long mount, you will see messages like:

portmap: server localhost not responding, timed out ubuntu

To solve the problem just do:

sudo apt-get install portmap

(check that this service will restart every time you restart your machine)

After that the mount of any nfs volume is really fast

---

### Post by powerflex on 2006-10-18
Portmap is definitly running.

The Problem was the Firewall. There has something changed on the client side in Ubuntu 6.06 and Debian Etch. The Solution is in this article:

[http://blog.basquiat.de/archives/305-NFS-und-Brandschutzmauern.html](http://blog.basquiat.de/archives/305-NFS-und-Brandschutzmauern.html)

powerflex

---

### Post by phoenix55 on 2007-08-03
Hi Everyone,
                    I'm using Ubuntu 7.04 and mounting an NFS filesystem was taking around 2 minutes. I installed the **portmap** service (which was not running) using the **synaptic** package manager and now the NFS mount is virtually instantaneous.

                    **Powerflex** do you know of an English translation of that German link ([http://blog.basquiat.de/archives/305-NFS-und-Brandschutzmauern.html](http://blog.basquiat.de/archives/305-NFS-und-Brandschutzmauern.html)) which attributes the NFS delay to the firewall. I'm interested in what they had to say in spite of the fact that my mount problem no longer exists.

phoenix55

---

### Post by powerflex on 2007-08-06
I have no translation of this article.

The Problem is: Never Versions of nfs use dynamic tcp/udp ports.
My Solution: Configuring nfs in old style (with static ports)
Howto and explanation in quoted german article.

powerflex


> **phoenix55 said:**
> Hi Everyone,
                    I'm using Ubuntu 7.04 and mounting an NFS filesystem was taking around 2 minutes. I installed the **portmap** service (which was not running) using the **synaptic** package manager and now the NFS mount is virtually instantaneous.

                    **Powerflex** do you know of an English translation of that German link ([http://blog.basquiat.de/archives/305-NFS-und-Brandschutzmauern.html](http://blog.basquiat.de/archives/305-NFS-und-Brandschutzmauern.html)) which attributes the NFS delay to the firewall. I'm interested in what they had to say in spite of the fact that my mount problem no longer exists.

phoenix55

---

