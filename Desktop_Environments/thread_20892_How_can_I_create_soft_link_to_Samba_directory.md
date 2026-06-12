---
title: "How can I create soft link to Samba directory"
date: 2005-03-19
forum: Desktop Environments
---

### Post by jeffjj on 2005-03-19
How can I create a soft link to a directory out on a windows directory using Samba? I have Samba all set up and it is working perfectly, however I would like to create a soft link to a certain folder so I can reach it like a regular folder. 

If I drag the folder into Nautilus and then tell it to create a link I get a unsupported operation error. Is there a way I could get this to work? From the command line if I try to use the ln -s smb://pathtofolder it still does not work.

To be more exact on what I am doing in case it helps is...we would like to use Ubuntu as a server for our group at work. What we would primary use it for is as a CVS server. However to ensure that our files are backed up each night we keep the actual files out on a Windows share folder. Currently we are doing this no problem with Cygwin. I know its a little screwy, but the rest of the company uses clearcase and this is the only way we were allowed to not use that. So, if I could create a soft link to that windows share (like Cygwin is doing now) then I would be set.

---

### Post by Dromio on 2005-03-19
[QUOTE=jeffjj]How can I create a soft link to a directory out on a windows directory using Samba? I have Samba all set up and it is working perfectly, however I would like to create a soft link to a certain folder so I can reach it like a regular folder. 

If I drag the folder into Nautilus and then tell it to create a link I get a unsupported operation error. Is there a way I could get this to work? From the command line if I try to use the ln -s smb://pathtofolder it still does not work.

To be more exact on what I am doing in case it helps is...we would like to use Ubuntu as a server for our group at work. What we would primary use it for is as a CVS server. However to ensure that our files are backed up each night we keep the actual files out on a Windows share folder. Currently we are doing this no problem with Cygwin. I know its a little screwy, but the rest of the company uses clearcase and this is the only way we were allowed to not use that. So, if I could create a soft link to that windows share (like Cygwin is doing now) then I would be set.[/QUOTE]
 You should mount the smb folder to a mountpoint.  See [http://ubuntuguide.org/#mountunmountnet](http://ubuntuguide.org/#mountunmountnet) and [http://ubuntuguide.org/#mountunmountnetworkfolder](http://ubuntuguide.org/#mountunmountnetworkfolder) for detailed instructions.

---

### Post by jeffjj on 2005-03-19
Thanks for the pointer. I will not be able to try it until Monday when I go into work, but that was exactly what I was looking for!

---

### Post by MountainX on 2008-01-25
> **Dromio said:**
> You should mount the smb folder to a mountpoint.  See [http://ubuntuguide.org/#mountunmountnet](http://ubuntuguide.org/#mountunmountnet) and [http://ubuntuguide.org/#mountunmountnetworkfolder](http://ubuntuguide.org/#mountunmountnetworkfolder) for detailed instructions.

These links don't go to the correct section and I am not able to locate the instructions. I would like to accomplish the same solution discussed above.

Do I have to first remove the "Places" server connection I have already defined (i.e., smb://user@192.168.1.1/Sharename)?

Does mouting the smb folder to a mount point replace the smb folder created via Places |Connect to Server?

My goal is to have access to a link to the MS Windows share from all my file dialogs within Ubuntu. Currently I have my share listed in the "Places" bar in the File Browser, but I do not have the ability to navigate easily to that MS Windows share from file dialogs. For example, when I download a file using Firefox and select save, I am forced to save it locally because I don't know how to access the smb share at that point. Any tips? Thanks.

---

### Post by MountainX on 2008-01-25
I just found this article:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

Is specifying the password in /root/.smbcredentials  a secure method? Is it recommended? Is there a better way?

What does "dmask=777,fmask=777" mean?

What effect on overall security does "chmod 700 /root/.smbcredentials" have?

Thanks.

---

### Post by MountainX on 2008-01-25
sudo mount -a
mount: wrong fs type, bad option, bad superblock on //192.168.100.1/MsShare,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Any ideas what this error means? Thanks.

---

### Post by qpieus on 2008-01-25
> **MountainX said:**
> sudo mount -a
mount: wrong fs type, bad option, bad superblock on //192.168.100.1/MsShare,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Any ideas what this error means? Thanks.
Do you have the smbfs package installed? smbfs is a program that allows samba shares to be mounted. Look in synaptic for it, or in a terminal type:

sudo apt-get install smbfs

---

### Post by MountainX on 2008-01-25
Thanks. I used Synaptic Package Manager to install smbfs and now I have my working link to my NTFS share. It's great.

I am really enjoying Ubuntu. I have only been using Linux (Ubuntu) for a few weeks, but I can already tell that I could never go back.

---

### Post by qpieus on 2008-01-25
Good job on getting it working. Welcome to the forum and to linux.

---

