---
title: "Shared folders usingGroups"
date: 2005-07-10
forum: Desktop Environments
---

### Post by lparsons on 2005-07-10
I have created a directory /home/Music that I have setup as a samba share.  I would like the folder to be readable and writeable by any user in the 'mediashare' group.

Things seems to work fine when I connect to teh share.  However, on the local machine I have problems unless I set the files to be readable by others.  I have created a group mediashare with my userid in it.  Then I setup the permissions to 0775.  However, I get an error that I dont' have permission to write to the files, even though I'm in the mediashare group.

/etc/group
mediashare:x:1002:lparsons,cparsons

ls -la
-rwxrwxr-x  1 nobody mediashare  6141952 2003-12-22 14:18 01-Statesboro Blues.mp3


/etc/samba/smb.conf
[Music]
   comment = Music Folder
   path = /home/Music
   public = yes
   writable = yes
   valid users = lparsons cparsons
   create mask = 0775
   directory mask = 0775
   #force user = nobody
   force group = mediashare
   available = yes
   browseable = yes


Any help would be greatly appeciated.

---

### Post by mabino on 2005-07-12
I'm having this issue too and it seems samba is irrelevant to the issue at hand.

> sudo groupadd shared
> sudo usermod -G shared myusername
> sudo mkdir shared-folder
> sudo chmod 775 shared-folder
> sudo chgrp -R shared shared-folder
> touch shared-folder/test
touch: cannot touch 'shared-folder/test': Permission denied
> ls -al | grep shared
drwxrwxr-x   2   root   shared   4096   Jul  12  08:57  shared-folder
> users-admin

Under the group tab 'shared' exists as a group.  Under its properties myusername is listed as a Group Member.  Just to be sure the problem also exists via GUI methods I used users-admin to create a second 'shared2' group.  I added myself as a member, clicked Ok and exited users-admin.

> sudo chgrp -R shared2 shared-folder
> touch shared-folder/test
touch: cannot touch 'shared-folder/test': Permission denied

Am I missing something, have I overlooked a bug report or is Ubuntu (5.04 Hoary, 2.6.10-5-386) seriously broken? ](*,)

---

