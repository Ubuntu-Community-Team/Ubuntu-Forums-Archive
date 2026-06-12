---
title: "Network Shares With Samba almost working"
date: 2009-04-06
forum: General Help
---

### Post by KrGAce on 2009-04-06
Hello all,

Here is my line from my /etc/fstab file..

#//192.168.1.2/hd2 /home/krgace/nmounts/hd2  smbfs   username=myusername,password=mypassword 0 0



With this uncommented and my real username and password put in, this will in fact mount correctly and I have an icon on my desktop (mounted), the problem arises when i try to access the share it tells me that I don't have permissions to view the contents.  On the server I have made sure that I do in fact have permissions.  I know this because if I go, Places, Network, and then SFTP File Transfer, put the same username and password in, it works fine.

Obviously I would like to mount my shares every time I log in, and not have to go through this process.  Can anyone help me?

Very much appreciated in advance.

AceMan

---

