---
title: "Shared Folder - Unhandled eror message:"
date: 2021-01-21
forum: Desktop Environments
---

### Post by slkamath on 2021-01-21
Hi,

While accessing shared folder getting message Oops! Something went wrong. Unhandled error message: Failed to mount windows share: Software caused connection abort. 

Please find the attached error message for your information.
[ATTACH=CONFIG]287778[/ATTACH][ATTACH=CONFIG]287779[/ATTACH]

OS: Ubuntu 16.04
[ATTACH=CONFIG]287777[/ATTACH]

Can someone help me to resolve this issue.

Thanks in advance.

---

### Post by ActionParsnip on 2021-01-21
Ubuntu 16.04 has very little support left. Less than 4 months. You may want to upgrade. Check your access in the Windows side (I assume you are accessing a Windows PC) and that access is allowed and the username/password used on the Ubuntu side is correct

---

### Post by CelticWarrior on 2021-01-21
> **ActionParsnip said:**
> Ubuntu 16.04 has very little support left. Less than 4 months. You may want to upgrade. Check your access in the Windows side (I assume you are accessing a Windows PC) and that access is allowed and the username/password used on the Ubuntu side is correct

This ^^^, there's no point in troubleshooting an about to be obsolete release.
And an [Intel® Xeon® Processor W3503]("http://Intel® Xeon® Processor W3503") is a 64-bit CPU. Why on Earth have you installed a 32-bit OS? As there's no upgrade for 32-bit going forward, just backup and install a currently support 64-bit release from scratch, end of story.

---

### Post by slkamath on 2021-01-22
Thank you so much for your information. 

We have shared folder via TrueNAS.

Thanks & Regards
Lokesh Kamath

> **CelticWarrior said:**
> This ^^^, there's no point in troubleshooting an about to be obsolete release.
And an [Intel® Xeon® Processor W3503]("http://Intel® Xeon® Processor W3503") is a 64-bit CPU. Why on Earth have you installed a 32-bit OS? As there's no upgrade for 32-bit going forward, just backup and install a currently support 64-bit release from scratch, end of story.

Thank you so much for your information. 

Thanks & Regards
Lokesh Kamath

> **ActionParsnip said:**
> Ubuntu 16.04 has very little support left. Less than 4 months. You may want to upgrade. Check your access in the Windows side (I assume you are accessing a Windows PC) and that access is allowed and the username/password used on the Ubuntu side is correct

Thank you so much for your information.

---

### Post by ActionParsnip on 2021-01-22
Does your NAS not share using NFS / SFTP too? Something better?

---

### Post by Morbius1 on 2021-01-22
> **slkamath said:**
> 
We have shared folder via TrueNAS.

Samba communicates through a series of dialects. According to the TrueNAS documentation: [https://www.truenas.com/docs/hub/sharing/smb/smb1/](https://www.truenas.com/docs/hub/sharing/smb/smb1/)
> SMB1 is disabled by default in FreeNAS and TrueNAS.


The samba client in Ubuntu 16.04 had the maximum smb dialect set to SMB1 ( Samba calls this NT1 ). The TrueNAS doesn't understand your request.

There are a couple of ways around this issue without enabling SMB1 on the TrueNAS:

One is a cifs mount where you can specify the smb dialect to use.

The other is through the samba client by editing /etc/samba/smb.conf and placing the following line under the workgroup = WORKGROUP line:
```
client max protocol = SMB3
```
You will need to reboot your Ubuntu machine.

The problem with this is that NetBIOS host discovery is broken so you will have to access the server and its share explicitly in your file manager. For example - in your file manager:
```
smb://truenas/share
```

[COLOR=#ff0000]**Note**[/COLOR]: If you don't have a samba server set up on your Ubuntu machine you may not have an smb.conf file. You can add one by installing smbclient:
```
sudo apt install smbclient
```

---

### Post by slkamath on 2021-02-02
> **Morbius1 said:**
> Samba communicates through a series of dialects. According to the TrueNAS documentation: [https://www.truenas.com/docs/hub/sharing/smb/smb1/](https://www.truenas.com/docs/hub/sharing/smb/smb1/)


The samba client in Ubuntu 16.04 had the maximum smb dialect set to SMB1 ( Samba calls this NT1 ). The TrueNAS doesn't understand your request.

There are a couple of ways around this issue without enabling SMB1 on the TrueNAS:

One is a cifs mount where you can specify the smb dialect to use.

The other is through the samba client by editing /etc/samba/smb.conf and placing the following line under the workgroup = WORKGROUP line:
```
client max protocol = SMB3
```
You will need to reboot your Ubuntu machine.

The problem with this is that NetBIOS host discovery is broken so you will have to access the server and its share explicitly in your file manager. For example - in your file manager:
```
smb://truenas/share
```

[COLOR=#ff0000]**Note**[/COLOR]: If you don't have a samba server set up on your Ubuntu machine you may not have an smb.conf file. You can add one by installing smbclient:
```
sudo apt install smbclient
```


Thank you for your response. I will check & update you.

Lokesh Kamath

---

### Post by slkamath on 2021-02-09
This will not work. I think ned to upgrade the OS then only it will work.

Lokesh Kamath

---

