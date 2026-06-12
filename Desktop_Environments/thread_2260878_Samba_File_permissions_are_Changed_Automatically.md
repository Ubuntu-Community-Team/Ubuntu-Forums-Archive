---
title: "Samba File permissions are Changed Automatically"
date: 2015-01-14
forum: Desktop Environments
---

### Post by raja_s_patil on 2015-01-14
Hello,

I am Using Ubuntu (Kubuntu) on server side for quite a long time and on desktop for about couple of years. Recently I have Installed Kubuntu 14.04 on Dell 1015 laptop with samba server from repositories. I have also created a Virtualbox XP vm which is suppose to emulate client to Main Kubuntu Server. I have created few samba shares to be accessed from XP VM and execute a Delphi (win32) application in XP from samba share which will access database on KU installation. 

The Samba share has Create Mast = 755 and directory mask = 755. The samba shares are used as mapped drives like e:, f:, h: etc. etc. in XP VM. When I copy or create any type of file from XP to these mapped drives on KU side permissions are rwxr-xr-x (755) as expected. The moment I execute some .exe on these pre-mapped drives the permissions change to rw-rw-rw- (666). How this is happening automatically ? The main problem is after this I can't execute same exe second time in XP and message "Windows cannot access the specified device, path, or file" is thrown. On KU side if i change permissions to 755 of same exe file It works again and same cycle is repeated.

Can somebody help me in this situation.

Thanks and warm regards

Raja

---

