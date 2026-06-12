---
title: "installation"
date: 2010-12-03
forum: Desktop Environments
---

### Post by saman fernando on 2010-12-03
Hi,
 
I am a first time user and want to learn Ubuntu.  I have installed the windows parallel version  in to one machine and was trying to install 10.10 to other machine. 
 
When I was trying to connect to the Internet the machine with windows parallel version it is not allowing saying that connectivity is disabled. Can any body explain?
 
When I was trying to install 10.10 using a CD image so the ubuntu will work along side with widows it installed. But my widows is perished as the widows partition was deleted. pl advise me how to overcome this problem. I can re-install windows through CD. I am afraid to install ubuntu again fearing the same problem. 
 
cheers

---

### Post by tom4everitt on 2010-12-03
> **saman fernando said:**
> 
When I was trying to install 10.10 using a CD image so the ubuntu will work along side with widows it installed. But my widows is perished as the widows partition was deleted. pl advise me how to overcome this problem. I can re-install windows through CD. I am afraid to install ubuntu again fearing the same problem. 
 

Hi, welcome new user!

When installing ubuntu from cd, like you tried, at one point you get the following options:

1. Install ubuntu on the entire disk
2. Install ubuntu beside current OS
3. Manual layout

(the order and the wording is probably a little different). 

If you want to keep Windows, it is really important that you don't pick 'Install on entire disk' but rather 'beside other OS' (or manual). Otherwise it will erase Windows. With this in mind your windows partition should be safe during install.

I didn't really understand you other questions, but that's probably because I'm not very experienced in these areas. Hopefully someone else will have an answer!

---

### Post by sikander3786 on 2010-12-03
Welcome to the forums :-)

I assume you mean a Wubi install of Ubuntu by saying "Windows parallel install". So you need to share files between them? Or you want to connect to the internet from your Wubi install?

Regarding a new install, I would recommend to install Windows again. Leave some unallocated space (that much that you want to assign to Ubuntu).

On the installer's partitioning page, choose Manual Partitioning. You basically need 2 partitions for Ubuntu.

1. Ubuntu Root partition, size > 8 GB at least, Filesystem ext4, Mount Point = '/'

2. Swap partition, size = RAM X 2

You can also add a separate /home partition if you want to. That would hold all your settings/configuration and personal files and is handy in case of a re-install as you won't need to extract your settings and important files from the root partition and then startover. Just re-install Ubuntu, don't choose to format /home and everything would be there as it was before :-)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

