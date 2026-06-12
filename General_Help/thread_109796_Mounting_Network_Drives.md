---
title: "Mounting Network Drives"
date: 2005-12-29
forum: General Help
---

### Post by dwessell on 2005-12-29
Hey all.

If connecting to a Windows Workgroup network.. Do you need to mount the network? Or does Samba do that work magically?

Thanks
David

---

### Post by FLeiXiuS on 2005-12-29
Ha, I wish things worked magically without you having to give them magical powers...

They aren't mounted, but they are viewable.  If you like to mount them...READ the jibber jabber below.

To start off, you will need smbfs.  
$ sudo apt-get install smbfs

Samba won't do it automatically.  You have to specify it to do so in your fstab file.  This is located at /etc/fstab.  You will need sudo access to write to it.  

To mount a file system temporarily.
mount -t cifs -o username=USERNAME,password=PASSWORD,uig=UID,gid=GID //IPADDRESS/SHARE /path/to/mount/to

Ok so let me explain the variables above.  

USERNAME is the username on the windows machine the share has access to.  If it's publically available the username will be 'guest'.  If this is the case then you do not need the 'password=PASSWORD' since it's PUBLICALLY AVAILABLE RIGHT!?  

The UID is the user's ID on your local machine in which to give permissions to the share.  For the default user on UBUNTU this number is 1000.  If you are using another username which you created after you installed, you will find this name in /etc/passwd.  

The GID has the same influence as UID.  GID is the group ID, basically the group to give local permissions to.  Default again is 1000 and you may look in /etc/group for other answers.

//IPADDRESS/SHARE is the remote share.  I like to use IP address, but for those who don't have a static network, meaning set IP addresses on their machines, then this won't do no good.  You could use the NetBios name.  If the computers name is fleixius with an IP of 192.168.0.65 and the share name is nick.  The remote shares location would be //fleixius/nick or //192.168.0.65/nick.

/path/to/mount/to is the location on the local machine where you want to mount the remote file system to.  This is up to you, just make sure you have permissions.  I generally like creating a folderin /mnt called network where I mount a network share.  Then I create a symbolic link from there to my home directory to make it easier accessing.

Example:
$ sudo mount -t cifs -o username=guest,uid=1000,gid=1000 //fleixius/nick /mnt/network

To mount on boot automically, MAGICALLY follow the following.

Open your /etc/fstab as sudo.
$ sudo gedit /etc/fstab

At the end of the file add something simular to the following.  By this I mean you can edit / remove parts which don't work for you.

//IPADDRESS/SHARE /path/to/mount to cifs defaults,uid=1000,gid=1000,username=USERNAME,password=PASSWORD,umask=007 0 0

Save and exit.

Voila, hope that helps.

/me waves the magic wand as I mount -a.

PS. sudo mount -a will remount the file systems located in /etc/fstab.  :-)

---

### Post by robert114 on 2006-03-24
defaults,uid=1000,gid=1000,username=USERNAME,passw ord=PASSWORD,umask=007 0 0 


Thanx that worked for me!

---

### Post by Zelut on 2006-04-11
What syntax can I use to automagically mount a windows share in fstab when I DO NOT need credentials? (ie; no username/password required on XP box &/or shares)

---

### Post by terryroe on 2006-04-12
kuyaedz,

I think you just need username=defaults,password=defaults.  See the article: [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

TR

---

### Post by CraiZE on 2006-04-14
I would like to extend the knowledge of this and append my own little Guide, since i kept being prompted for the password upon boot, and didn't like storing it in /etc/fstab (which every user can read!), so here we go :)

1) Install Samba FS

Type: sudo apt-get install smbfs

2) Make your Samba Login Info secure :

Open up any Terminal with the user you want to give Write Access

```

cd $home
echo username=mywindowsusername > .smbpasswd
echo password=mywindowspassword >> .smbpasswd
chmod 600 .smbpasswd

```

Replace **mywindowsusername** with Your Windows Username
Replace **mywindowsPassword** with Your Windows Password

3) Find out your UID (User ID) & GID (Group ID)

type "id" in the CLI (Command Line Interface , such as gnome-terminal)
It should return a line telling you your ID and Group ID, it was "1000" for me :)

4) /etc/fstab Entry:

Now here is a sample:
```
//192.168.1.1/c /media/Server-C smbfs defaults,uid=1000,gid=1000,credentials=/home/craize/.smbpasswd,credentials=/home/craize/.smbpasswd,umask=777 0 0
```


This will connect to the Samba Server on 192.168.1.1, and tries to mount the shared folder "c" to /media/Server-C using the UserID 1000, group ID 1000 and reads the login and password from the credentials file. This way no more prompts, yet it remains secure :)

5) Mount all of your entries in /etc/fstab at once

Type: sudo mount -a

And that's it! :)

---

### Post by Robgould on 2006-04-20
I added my remote windows shares to fstab like this
 
```

//192.168.0.100/c  /mnt/winc  smbfs  rw,username=XXX,password=xxx,uid=1000,gid=1000  0 0 

```
 
Then did
 
```

sudo mount -a

```
 
This worked great.  But when I restarted the "mounting remote filse systems" failed.  So did the mount -a again....worked again.
 
 
I changed my fstab like above
 
> 
//IPADDRESS/SHARE /path/to/mount to cifs defaults,uid=1000,gid=1000,username=USERNAME,passw ord=PASSWORD,umask=007 0 0

 
and mount -a worked this way too, but mounting failed on reboot again
 
I thought maybe it was a permissions issue so I did 
 
```

sudo chmod -R 777 /mnt

```
 
Still no luck.
 
Again, as soon as I am up in gnome performing sudo mount -a mounts my sahres, but during reboot the mounting fails everytime. 
 
Is this a Dapper bug?  Anyone know how to fix it?

---

### Post by CraiZE on 2006-04-20
is that a copy paste?

cause you have "pass word=" in your paste.....

---

### Post by Robgould on 2006-04-20
I fixed the"password"  - just does not work till after boot

---

### Post by Robgould on 2006-04-20
I works now.  I did a dist-upgrade and now it works.

---

