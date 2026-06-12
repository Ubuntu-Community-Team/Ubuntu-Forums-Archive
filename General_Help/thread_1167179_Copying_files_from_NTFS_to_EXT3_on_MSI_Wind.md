---
title: "Copying files from NTFS to EXT3 on MSI Wind"
date: 2009-05-22
forum: General Help
---

### Post by PJBLinux on 2009-05-22
Hi All, 

I am running 9.04 (fully patched) base install on an MSI U100 Wind Netbook, and I am trying to copy files by opening up a connection to my server by browsing the network, and selecting a folder on the remote server, and using simple copy / paste to my desktop. 

I get a file transfer of 700mb starts very quickly and then gradually slows down, then about half way through it stops completely, it still has a time estimated. Yet no data is moving. 

The remote server is an HP DL145 G2 running Windows Server 2003 R2 SP2
I am connected via a single switch (gigabit 3com) to it 
I logged into the remote server as Administrator
I am the owner of the remote folder and I have reset all permisions for Administrators group on the Windows side to give me Full Control

I have tried copying files from a few different servers and even a windows XP box I have sat next to me, and the same slow-down then stop occurs. 

I have seen several posts on slow down and performance issues on using USB and CDROM and I am wondering if this could also affect Network transfers from a server to the local hard disk. 

Thanks for your help in advance. 

Patrick :)

---

### Post by pricetech on 2009-05-22
winders is that way.  It will frequently choke on large files, especially over the network.

Is this a single file or a set of files ??  If a set, break them down into groups of 100 meg or less (preferably less) and move them a few at a time.

Have you left it copying overnight to see if it finishes ???  I've had to do that with winders before.

---

### Post by Ugluk on 2009-05-23
Don't spread FUD. Windows easily copies 1GB+ files over the network.

To OP: Try torrent or rsync client for Windows if you suspect your network is unreliable.

---

### Post by PJBLinux on 2009-05-24
I tried using different methods as you suggested, I have tried grsync and it slowed down a lot but didnt completely stop like the nautilus copy did. 

I dont know if this is important or not but I am copying many small files, all less then a few mb in size.
Fragmentation on the windows end is < 1% completely. 

I saw a post on copying being slow from a flash usb memory and a cdrom to the ext3 partition, and I am wondering how I can enable DMA mode on my laptop hard disk so I can see if the issue is my local disk bogging down when copying lots of small files over SMB. 

Side point but I have a windows xp pro sp3 dual boot and this copies the same files in a matter of 20 minutes at almost 5mb per second. i get about the same initially then tapers of to 600-700kbps with Nautilus grsync manages a healthy 1-2mb all the way after an initial burst of 4-5mbps. 

I replaced the switch and tried new cables, and I am the only person using this server, (it having dual 1gb connections as I mentioned, and the switch being a gigabit, my netbook is a modest 100mb connection, so I should get about 5-10mbps at least in ubuntu as I do from windows xp sp3.  

Any ideas or suggestions are welcome thanks!!! 

Patrick

---

### Post by PJBLinux on 2009-05-27
The fastest way I have found to connect and transfer files from a Windows 2003 or XP server side machine to a Linux desktop client machine is as follows. 

Download and install SMBFS with the command (sudo apt-get install smbfs) 

Run the commands as follows

Make a directory as follows (the name can be whatever)
mkdir ~/mywinfiles

Mount the servers remove volume to the local directory, use the [-o] parameter then the [username] parameter then an [=] sign and in quotes "" enter your username and domain name ergo "patrick/myADdomain"

smbmount //server/share ~/mywinfiles -o username="user/domain"

Download and install GRSync with the command (sudo apt-get install grsync) 

Click Applications, System Tools, GRSync

Select source as the ~/mywinfiles folder and select destination as ~/Desktop/MyCopy
(Again the destination can be anywhere, I work from the desktop a lot so this works for me) 

Run the sync, and within a few minutes I got all 36,000 files, 560mb to my Ubuntu desktop. 

Nautilus took over an hour and stopped completely several times. So I have a fix for now, and based on what I have read here at [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/84782](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/84782) this is about the only way to deal with this connection issue when using windows servers. 

Thanks for the excelent help and wonderful forum's I would be lost without them.

---

