---
title: "PXE client requests an IP address twice"
date: 2009-03-01
forum: General Help
---

### Post by pla on 2009-03-01
Hi 

I have a working PXE client with a minor problem. The problem is late in the boot process, it hangs when trying to mount NFS drives in the /etc/fstab file. After many hours of troubleshooting I have discovered that the PXE client is requesting an IP address from the DHCP server twice. Once after power-up and then again sometime later during the boot. I am assuming that this could be causing the problem with mounting the NFS drives during the boot. The drives mount just fine after the boot with ```
sudo mount -a
```. 

Here is a link to a Wireshark screen scrape showing the two DHCP requests. [http://tinyurl.com/agk4rl]("http://tinyurl.com/agk4rl"). 

In the [DisklessUbuntuHowTo]("https://help.ubuntu.com/community/DisklessUbuntuHowto") document it states you don't want the system to bring up the Ethernet interface since it is already configured by the kernel. So, in my /etc/network/interfaces file I have ```
iface eth0 inet manual
``` Apparently the system is still trying to configure eth0. 

What could be causing the second DHCP request? 

Thanks, PLA

---

