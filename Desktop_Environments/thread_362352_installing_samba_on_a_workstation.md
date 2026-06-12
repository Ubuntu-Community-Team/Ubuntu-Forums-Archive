---
title: "installing samba on a workstation?"
date: 2007-02-15
forum: Desktop Environments
---

### Post by luminex on 2007-02-15
Hi all, i am a teacher and currently use Edgy in my school lab (thin clients use dual booting with either Windows 98 or Edubuntu 6.10. The network has a smb server, which allows us to access windows files from Edubuntu. That's fine. But how can i do that at home where Windows and Edubuntu are just installed on a single workstation. Is Samba just for servers?

How do i install samba or a similar software on Linux (i am not connected to the internet and therefore cannot download and install from the edubuntu bundle)

Thanks in advance for your help.:)

---

### Post by mssever on 2007-02-15
Yes, you can install samba at home. The only difference between a server and a desktop install is what software is included by default. But I don't know whether Samba is included on the CD. If it isn't, you'll have to either connect to the Internet or manually download the correct .deb files from another computer and transfer them.

However, if your home computer isn't part of a network of some sort, then samba won't do you any good. Just mount the partitions directly. See [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131). To access your Linux ext2 or ext3 partitions from Windows, there is a free driver available. Google it, because I don't remember what it's called.

---

### Post by luminex on 2007-02-16
Thanks for your kind help and the great thread! I have a USB modem but it does not work with edubuntu. Hopefully i will turn this workstation into a small server for my home, but i'm going to need to install a wireless card and create an ethernet connection.:)

---

