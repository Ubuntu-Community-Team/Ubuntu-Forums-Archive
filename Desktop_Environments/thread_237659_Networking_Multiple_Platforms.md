---
title: "Networking Multiple Platforms"
date: 2006-08-16
forum: Desktop Environments
---

### Post by ryan.stults on 2006-08-16
I am currently running Win. XP and Ubuntu 5.10 (which I am going to upgrade, so if its different with the newer one, either one is fine) dual boot.  My brother has a Mac OS 10.3.9.  We have the Win and Mac networked, but I also want to add the Linux to the network.  I'm sure I won't be able to access the windows files that way, which is fine, I atleast want the Linux and Mac to talk. Can someone help me????](*,)

---

### Post by 505 on 2006-08-16
Of course you can access the Windows files from your Linux computer. You need samba for that. That program allows you to browse and mount windows shares and share files on your linux machine so Windows can browse them.
I don't know how you set up browsing between mac and windows. If you use another protocol for that, just search for it in combination with linux. Big change it's available.

A great guide for setting up Samba (an a lot of other things) can be found at [http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server](http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server)

---

### Post by ryan.stults on 2006-08-16
> **505 said:**
> Of course you can access the Windows files from your Linux computer. You need samba for that. That program allows you to browse and mount windows shares and share files on your linux machine so Windows can browse them.
I don't know how you set up browsing between mac and windows. If you use another protocol for that, just search for it in combination with linux. Big change it's available.

A great guide for setting up Samba (an a lot of other things) can be found at [http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server](http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server)

I will be able to see/use the windows file on ubuntu and see/use the ubuntu files on windows even though they are on the same machine????
Also I reall just need to know how to setup a network on Ubuntu.  I can probably handle the rest *ip address and such*

---

### Post by 505 on 2006-08-16
> **ryan.stults said:**
> I will be able to see/use the windows file on ubuntu and see/use the ubuntu files on windows even though they are on the same machine????
Also I reall just need to know how to setup a network on Ubuntu.  I can probably handle the rest *ip address and such*

Mmm, I missed the part about dual boot. Linux can read the windows files just fine. Writing is a bit experimental (see ntfs-3g if you want to write to your windows drive from linux).

If you [install a special program](http://www.fs-driver.org/) in Windows you'll also be able to read and write from you linux drive from windows.

Because they are all 'just drives' to the OS, you can share them without a problem.

Setting up a network in ubuntu is very easy. I suggest reading the URL provided in my first post.

---

