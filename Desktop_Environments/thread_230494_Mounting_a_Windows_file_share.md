---
title: "Mounting a Windows file share"
date: 2006-08-06
forum: Desktop Environments
---

### Post by srunni on 2006-08-06
EDIT: Right now I need to know why I have to ```
sudo mount -a
``` every time I log in before I can access smb://kakkarot/music from /mnt/music and how I can make this automated.

Hi,
I use the Places -> Connect to Server feature to access a Windows file share on my LAN, but it doesn't have a local folder location. I've heard that you can solve this problem by editing the /etc/fstab file, but I'm not sure exactly how. I searched on Google/these forums but couldn't find anything that worked for me.

Here are the specifications regarding my network share:

To get to the share using Samba, I have to type smb://kakkarot, or accessing it using the Places -> Connect to Server feature. In that I choose Windows file share and put kakkarot for "server". I leave everything else blank, and it works. I want to access a folder called "music", (aka smb://kakkarot/music). The LAN IP of the Windows computer is 192.168.1.100. I want to mount the "music" folder to /mnt/music. If any other information is needed, please tell me.

Thanks in advance for the help!!!!

---

### Post by srunni on 2006-08-06
Any ideas?

---

### Post by srunni on 2006-08-06
Could someone please help? I really need this problem fixed.

---

### Post by vaskark on 2006-08-06
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read](http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read)

This might be what you are looking for.

---

### Post by srunni on 2006-08-06
This is what I added to /etc/fstab:
"//192.168.1.100/music    /mnt/music smbfs  credentials=/root/.smbcredentials    0    0"

However, when I used
```
sudo mount -a
```

I got:

mount: wrong fs type, bad option, bad superblock on //192.168.1.100/music,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by sonybuff on 2006-08-09
Make sure you have smbfs installed

# sudo apt-get install smbfs

---

### Post by tronica on 2006-08-09
check out the post i made on there
[http://ubuntuforums.org/showthread.php?t=233051](http://ubuntuforums.org/showthread.php?t=233051)

---

### Post by srunni on 2006-08-11
sonybuff:
I've already done that

tronica:
The thread you linked was about a problem where the Windows file share couldn't be found at all. I can find my share just fine; I just have to do ```
sudo mount -a
``` every time I want to access the files.

---

### Post by Irony on 2006-08-11
You should use;

*Places >  Network Servers*

to see Windows shared folders.

---

### Post by srunni on 2006-08-11
Irony:
I don't think you fully read my initial post. I'm trying to mount the Windows share to /mnt/music. You can't make a shared directory the collection directory for amaroK unlesss it's mounted locally, so I'm trying to mount smb://kakkarot to /mnt/music. Places -> Network Servers is not a viable solution to this problem. Right now, I just need to find out why I need to ```
sudo mount -a
``` every time I log in before I can access the music through /mnt/music and how I can fix this problem.

Note: I already tried adding "sudo mount -a" to System -> Preferences -> Sessions -> Startup Programs.

---

### Post by miket on 2006-08-15
I was receiving the same message mounting a smb share, but it was resolved when I installed smbfs.  Since it sounds like you have already installed that package, here is the fstab line that I am using.  I do not use the credentials option.

//frodo/SharedFrodo  /frodo  smbfs  noauto,username=guest,password=,rw  0  0

---

### Post by srunni on 2006-08-18
Thanks a lot miket, I'll have to look into that (once my Windows box is working again ;) ).

---

