---
title: "Xfce Samba from Run (smb://)"
date: 2006-09-28
forum: Desktop Environments
---

### Post by Waqas Ahsan on 2006-09-28
hi
i just installed xubuntu-desktop on my dapper machine and it seems to be working fine (though i havent messed with it much).However there is one problem i cant figure out how to access samba shares in GNOME it was pretty simple:
Alt-F2 ---> smb://[network ip] 
but this same pocedure results in an error in Xfce.

So how do i use samba from "Run" in Xfce???

---

### Post by kidders on 2006-09-28
Hi there,

What you're describing works in Gnome and KDE by virtue of a complicated architecture of libraries that allow them to handle samba filesharing transparently. Xfce is much more lightweight ... features like that have been deliberately excluded.

---

### Post by Waqas Ahsan on 2006-09-28
thanks for the reply :)
yeah its understandable since xfce is striving to lightweight.
i tried out Xfsamba: using its go to feature to access remote ip's but Xfsamba didnt show any shares of the remote computers and also there was a some trace error in smbclient.c file message shown in terminal. The shares of computers geographically and also in manner of networking nearer to be show up fine.
Any idea whats happening?

---

### Post by kidders on 2006-09-29
None at all :-(

Could you post the errors you get?

---

### Post by Waqas Ahsan on 2006-09-29
The error i got in terminal was:

TRACE: undefined error at smblookup.c

---

### Post by dannyboy79 on 2006-09-29
i have xubuntu and use smb just fine. On Xubuntu Dapper Drake, Samba can be installed by typing

apt-get install samba
The software is stored on the CD.


--------------------------------------------------------------------------------

/etc/samba/smb.conf
Supposing you wanted to set up a shared folder called projects . Your smb.conf entry might contain the following fragment


workgroup = CAPCIS # or whatever workgroup you decide on
[projects]       comment = Projects       path = /home/shared/projects       writeable = yes       valid users = @users       create mask = 2660       directory mask = 2770

This will give users access to this directory, and they'll be able to read and write to it.

--------------------------------------------------------------------------------

User accounts
You will probably need to create a samba account for a user:
smbpasswd -a username
You will be prompted for a password

--------------------------------------------------------------------------------

Start/stop/restarting samba
On Xubuntu Dapper Drake, to restart samba you would type, as root:

/etc/init.d/samba restart
Starting and stopping is achieved by replacing the word restart with either start or stop . 

--------------------------------------------------------------------------------

Mounting directories
If you want to mount directories on your Linux drive that belong on remoter machines, (to use smbclient ,  smbmount etc.), you will also need to install package smbfs . A typcial way of doing it might be:


mkdir /mnt/projectschmod a+w /mnt/projectssmbmount  //192.168.30.3/projects /mnt/projects -o username=NNN,password=NNN,workgroup=NNN,uid=NNN,guid=NNN

You can umount by typing

umount /mnt/aber1

---

### Post by kidders on 2006-09-30
> **Waqas Ahsan said:**
> undefined error at smblookup.cAre you trying to access samba servers on different networks?

dannyboy79's description is very nice ... when dealing with Samba shares, I always just mount them like he describes. This business Gnome & KDE have started to play around with, of accessing shares without really mounting them, seems terribly confusing to many users!

---

### Post by Waqas Ahsan on 2006-09-30
thanks for trying to help guys :). 
Yeah dannyboy79's post is pretty descriptive but its that i have already done all that he mentioned i have samba up and running(it works fine under GNOME) even under Xfce as i said i can see the shares of people closer to me on the network.
As far as mounting shares is concerned it is definitely right but i cant mount something i dont know about now can i :)? the problem remains: i can nnot view the shares through Xfsamba.

---

