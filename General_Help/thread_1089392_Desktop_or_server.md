---
title: "Desktop or server?"
date: 2009-03-07
forum: General Help
---

### Post by im_jakes on 2009-03-07
What edition should i choose?

What the server should do:
-Squezze Center
-FTP server
-News download (NZB download)
-Raid (2x 1TB disks)
-Support Wake On Lan
-Support Wake On Wan

Computer spec:
KABINET CHENBRO ES34069 MINI-ITX STORAGE SERVER 12
MB VIA EPIA-SN 18000G 1.8 GHz WITH FAN MINI-ITX PC
2x RAM Corsair 1 x 2 GB1 x 2 GB (2 GB) / DDR II SDRA
2x HD SATA2 1 TB WD CAVIAR GREEN POWER 16MB 7200RPM

How do i setup raid in ubunto (server or desktop edition)

Thanks in advance
-Jacob

---

### Post by martrn on 2009-03-07
Software Raid or Hardware Raid.  Software Raid is one sure far way to slow your workstation/server down to a bare craw.  There are also diffrent type of RAID withing that sphere.  Your motherboard might?? (mine does) have hardware raid that complete manages the mirroring of discs and is fast.

See [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/") for Setting up software RAID in Ubuntu Server.  If its hardware RAID then look at your hardware supplier.

Most of what you are asking about can be done in a terminal and on a server, are you going to be running it header-less (without a monitor) or installing a desktop ?

If you are installing a light desktop just install the desktop version of ubuntu/xubuntu but get the alternative install disc.

If you are running headerless (or need no X11 gui) install the server version and 'sudo apt-get install linux-686'  to install a diffrent kernel or leave it with the server kernel.

---

### Post by albandy on 2009-03-07
It's a better option to install server because of the kernel modifications for server. If you need graphical environment you can install desktop in server simply typing "sudo apt-get install ubuntu-desktop"

---

### Post by martrn on 2009-03-07
Install a desktop version and it is really quite the same as the server version.  One change of the kernel to a server kernel and a couple of installs (apache/php/msql) and hey presto you have a server version with a desktop.

```
sudo apt-get install linux-image-server linux-server 
```

---

### Post by albandy on 2009-03-07
> **martrn said:**
> Install a desktop version and it is really quite the same as the server version.  One change of the kernel to a server kernel and a couple of installs (apache/php/msql) and hey presto you have a server version with a desktop.

```
sudo apt-get install linux-image-server linux-server 
```

Try to install desktop in some raid-hw configured proliant models.

---

### Post by martrn on 2009-03-07
> **albandy said:**
> Try to install desktop in some raid-hw configured proliant models.

If you are installing software RAID make sure you use the alternative CD if you are installing a desktop and need one straight up.

[URL="https://help.ubuntu.com/community/Installation/SoftwareRAID"]
https://help.ubuntu.com/community/Installation/SoftwareRAID[/URL]

---

### Post by curadebt on 2009-03-07
You should use server which can perform functions of FTP server, Raid, Support on On Lan and Wan.

---

