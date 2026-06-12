---
title: "CIFS Mount Issues"
date: 2010-11-23
forum: Desktop Environments
---

### Post by peshko-lnx on 2010-11-23
Couple of things.

I use 10.10 an my server is basically Buffalo NAS.

Here is my fstab line:
//xxx.xxx.xxx.xxx/myfolder       /media/test     cifs     rw,noperm,iocharset=utf8,credentials=/etc/.smbcredentials,file_mode=0777,dir_mode=0777,users  0 0

smbcredentials contains username and password.

It mounts it successfully, but with the wrong owner. If I mount it with  root, owner of every file is root, if I mount it with user1, owner  of  every file and directory is user1.

1. It seems that it disregards .smbcredentials. If I don't specify  .smbcredentials, it asks for a pwd, but I can put any random key  combination and it would be ok and mount the remote share

2. Unmount from the user1 is impossible. Always have to umount with  root. If I try to umount with user1 I get an error that says:


user1@ubuntu10-lap:~$ mount /media/test
user1@ubuntu10-lap:~$ mount
.
.
//xxx.xxx.xxx.xxx/myfolder/ on /media/test type cifs (rw,mand,nosuid,nodev,user=user1
 
user1@ubuntu10-lap:~$ umount /media/test
umount: /media/test mount disagrees with the fstab

3. Shutdown hanging when cifs is mounted is permanent. There seems to be  no workaround. I applied MANY solutions, but seems that there is no  permanent solution.

My question is - is there a solution to any of these problems that you might be aware of?

Thanks!

---

### Post by Boondoklife on 2010-11-24
Why not just map the drives when the user logs in? Is there a reason you trying to do it via fstab instead?

You can check here for a mapping script: [_p_9322776_:c77_]("http://ubuntuforums.org/showpost.php?p=9322776&postcount=77")

---

### Post by peshko-lnx on 2010-11-24
> **Boondoklife said:**
> Why not just map the drives when the user logs in? Is there a reason you trying to do it via fstab instead?

You can check here for a mapping script: [_p_9322776_:c77_]("http://ubuntuforums.org/showpost.php?p=9322776&postcount=77")

This is interesting. I'll look at it. On the site it describes where to put the gnome-samba-mount-startup.desktop. Where do you put gnome-samba-mount-startup? It seems I need to edit gnome-samba-mount-startup as well. Any specific syntax?

Thanks again!

---

### Post by Boondoklife on 2010-11-24
Please go into the file and change the paths that are to be mounted and  get rid of unneeded entries. Lines 47-51 of the file, you can simply  delete lines that you dont need or add more just follow the numbering  scheme (0,1,2,3,n...). The syntax is outlined in the file.

To make the script available to all run
 	Code:
 	sudo cp ~/Downloads/gnome-samba-mount-startup /usr/bin
sudo chmod 755 /usr/bin/gnome-samba-mount-startup

---

### Post by knattlhuber on 2010-11-29
If you wanna use /etc/fstab, you could try:

```
//192.168.1.4/myfolder /media/NASshare cifs guest,rw,user,uid=1000,gid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

You may have to change *uid*/*gid* to whatever your user/group IDs are. You can find that info in the passwords file:
```
cat /etc/passwd
```

A "manual" mapping option option without /etc/fstab is described [here]("http://ubuntuforums.org/showthread.php?t=1186877").

---

### Post by Boondoklife on 2010-11-29
@knattlhuber The page you linked to is the same one that I gave him a link for already, I added a script to it about 70 posts in but the author for some reason wont put it on the main page. If you haven't seen the script you should click the link and try it out.

---

