---
title: "File system on portable storage device."
date: 2009-04-16
forum: General Help
---

### Post by satimis on 2009-04-16
Hi folks,


Ubuntu 8.04


I have an USB external cabinet mounted an ATA 40G HD with 2 partitions running.  I'll use it as portable storage device keeping working data.  Most of them are .txt, .jpg, .pdf, etc. files.  The said device is used mainly on Linux PC.  What will be the ideal system to be formatted on it?  FAT32?

If I expect the data can be read on M$Windows PC then what ideal system shall I use/format?

TIA


B.R.
satimis

---

### Post by s.fox on 2009-04-16
Hi,

I would look at [NTFS ]("http://en.wikipedia.org/wiki/NTFS")file system.   

Guide on how to do  this on Ubuntu can be found [here]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

-Ash R

---

### Post by satimis on 2009-04-16
> **Ash R said:**
> Hi,

I would look at [NTFS ]("http://en.wikipedia.org/wiki/NTFS")file system.   

Guide on how to do  this on Ubuntu can be found [here]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

-Ash R
Hi Ash,


Thanks for your advice and URL.

Another thought, if all Linux and Windows PCs are on the same LAN.  Can I run ssh and scp to do the job?  Can I install and run ssh and scp on Windows?  TIA

B.R.
satimis

---

### Post by uncle-c on 2009-04-16
You can use Putty (SSH for XP) to login to Linux from XP and if required use its related programs ; pscp and psftp; secure copy and secure ftp ( if you are running a ftp server on the linux box) for file transfers.

---

### Post by satimis on 2009-04-16
> **uncle-c said:**
> You can use Putty (SSH for XP) to login to Linux from XP and if required use its related programs ; pscp and psftp; secure copy and secure ftp ( if you are running a ftp server on the linux box) for file transfers.
Hi uncle-c,


Thanks for your advice.

Any foreseeable risk installing Putty on XP?  All Windows PCs are quite fragile, easy to crash.  

All Linux PCs here are running both ftp server and client.

Would Samba be an easier solution?  However I must install Samba on all PCs which needs lot of work.

B.R.
satimis

---

### Post by uncle-c on 2009-04-16
I'm sure most people on here would vouch for Putty SSH. It is a standalone executable file ( as are pscp and psftp) and will do no harm whatsover to your XP system. I have been using it for many years - no problems at all.
If you just want to share XP files with you linux machines then there is no real configuring to do. Just go into your XP and set the directory which contains all the files you want to share to "share on network." You should be able to access this using the ---> PLACES --> Network OR ---->PLACES-->Connect to Server from your Ubuntu panel.
If you want to share files on your Linux box with an XP  machine then you will have to set up a Samba share, tutorials on which are easily found in the very helpful forums here. If you just want to login and transfer files from one system to another every now and then, then just stick to Putty / pscp/psftp but if you have a lot of different users who need access to a group of files on a regular basis ( and these files are stored on a linux box)  then set up samba and "map network drives" when on XP so that the XP users can access the linux share. Info on mapping drives is all in the tutorials. You don't need to install anything on XP, just need to do some reconfiguring and making sure specific ports are open.

---

