---
title: "Auto Mounting Network Shares"
date: 2005-06-27
forum: Desktop Environments
---

### Post by MajorDmp on 2005-06-27
Oh man.

   I tried not to post a question but been running in circles. Lets say, I have to give thanks to all those out there who spend time answering questions. I've learned a lot of just reading but I can't seem to find the solution to this problem.

  I finally figured out how to mount windows network shares using Samba. I mounted the share to a directory and everything is working great. I just can't figure what file to edit so that upon reboot, it will remount those shares. 

Any Takers?

---

### Post by angkor on 2005-06-27
Maybe your answer is in [here](http://www.ubuntuguide.org/#windows) somewhere...the file you're looking for is /etc/fstab.

---

### Post by FLeiXiuS on 2005-06-27
[QUOTE=MajorDmp]Oh man.

   I tried not to post a question but been running in circles. Lets say, I have to give thanks to all those out there who spend time answering questions. I've learned a lot of just reading but I can't seem to find the solution to this problem.

  I finally figured out how to mount windows network shares using Samba. I mounted the share to a directory and everything is working great. I just can't figure what file to edit so that upon reboot, it will remount those shares. 

Any Takers?[/QUOTE]

You best bet would be to use /etc/fstab.  This file controls what will be mounted at boot.  So you have a smb share which you would like to have automount.  Ok, assuming you already have a directory for each share to be mounted to we'll procede.

Open a terminal in some manner.  ( Applications > System Tools > Terminal )

Now time to edit the fstab.
```
$ sudo gedit /etc/fstab
```

In here you'll see what may look like gibberish to you, but it's very valuable.  At the end of the file is where you will be making your mounts.  I'll show an example of mine...
```
#network shares
//192.168.0.91/z        /mnt/network/z  smbfs   username=guest,password=,umask=007,uid=1000,gid=1000    0       0
//192.168.0.91/x        /mnt/network/x  smbfs   username=guest,password=,umask=007,uid=1000,gid=1000    0       0

```

This takes the shared folders z and x on my Windows XP machine with an IP of 192.168.0.91 and mounts them to wherever I specify.  (/mnt/network/z or /mnt/network/x)  You may have to change the username and password option.  But if your shares are on a windows XP machine, then you can leave them as is.  Next we'll look at permissions, please remind you self that the fstab mounts as root.  So normal users won't have access.  So lets set some permissions.
```
//192.168.0.91/z        /mnt/network/z  smbfs   **username=guest,password=,umask=007,uid=1000,gid=1000**    0       0
```
Umask is comparable to chmod.  Except it's backwards.  A umask of 007 is a chmod of 770.  IE: Umask=022 : chmod=755.  Simple eh?  Next, UID / GID.  UID=User ID, which can be determined by /etc/passwd.  A UID of 1000 is the default ubuntu user given sudo rights.  As well as the GID of 1000.  GID=Group ID, which can also be determined by /etc/groups.  Change if necessary.  If not, no worries.  The last parameters are really inconsistant to network shares.
```
//192.168.0.91/z        /mnt/network/z  smbfs   username=guest,password=,umask=007,uid=1000,gid=1000   ** 0       0**
```

After all is done, save then exit.  That should be all.  If you would like to test your new mounts.  Unmount them if they are currently mounted, then in a terminal type..
```
$ sudo mount -a
```
This will mount everything in the /etc/fstab.  If all goes well SWEET!!  Congrats!! If not, please post again...lol.

---

### Post by MajorDmp on 2005-06-28
Great! This worked fabulously! 

  I am little anal on security. Is there a way to do the same thing without the password being in cleartext?

Thanks in Advance

---

### Post by lonetree on 2005-07-01
I may be wrong about this, but the /etc/fstab can only be viewed with the rights of the root user (i.e the sudo user),normal user will not be able to get access to the file. 

So, if I'm wrong about this, please correct me.

Regards,

---

### Post by rwabel on 2005-07-01
for security reason I've put username and password in a separate file
my fstab entry looks like that
```
//wabel/g       /mnt/wabel/g    smbfs   credentials=/etc/fstab-winsvr,uid=rwabel
```

and the fstab-winsvr looks then like that
```
username=your username
password=your password
```

Maybe this isn't the best way, but it's working. If there is another or a better way to do it, please let me know

---

### Post by slada on 2005-07-21
FLeiXiuS,

Your setup worked perfectly.  The question I am trying to solve is how to mount two different shares like you did but with different permissions for different users.  I tried changing the umask and the gid but nothing works.  In fact, once I run mount -a and mount the two shares, I can't even change the permissions with root and everythng defaults to chmod 755.

Here is the line I put in fstab:

//baserver01/Staff /mnt/StaffDocs smbfs username=*windowsusername*,password=*windowspassword*,umask=007,uid=1000,gid=1002 0 0

However, I can still access the share from a different user account as well as who is not part of gid 1002.  

Also even though I set th permissions at umask=007 which should be the same as chmod=770, the permissions default to 755 and I cannot change them even with the owner of the folder they are mounted to.   :-x 

Any help would be appreciated. 

David

---

