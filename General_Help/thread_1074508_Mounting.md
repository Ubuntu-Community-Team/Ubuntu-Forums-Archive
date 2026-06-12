---
title: "Mounting"
date: 2009-02-19
forum: General Help
---

### Post by pasha07 on 2009-02-19
I have asked this question before and a lot of people have been very helpful (thank you) and I have searched a lot but I don't seem to find an answer. I am probably not explaining it well. So I thought I would give it another shot. 

I have a network storage device. USR8700 (@ 192.168.1.100). 

Currently I have it added to fstab and it mounts at every startup:

```
//192.168.1.100/public /media/usr8700 cifs username=***,password=***,_netdev,uid=1000,gid=users 0 0 
```

I am trying to figure out a way so I have an icon under places or a desktop icon that when I click it mounts the network drive, and not at startup. Similar to how Ubuntu mounts a windows partition. 

Any help would be appreciated. 

thanks

---

### Post by insineratehymn on 2009-02-19
Is the external ext3 or fat32?

---

### Post by pasha07 on 2009-02-19
Thanks for the reply. I am not really sure how I can find out, USR8700 has 4 250G hard drives that is setup to look like as one. 

In the manual it says for windows use CIFS protocol and for linux/mac use NFS protocol. 

Does that help at all?

thanks again

---

### Post by perrti-y02 on 2009-02-19
If you go into network on the file browser can you see the drive? What I mean by that is open any old directory then on the left hand pane there should be a tab saying network. Navigate through it (probably through "Windows Network") and you may well see this device. Then just drag it onto the desktop.

---

### Post by pasha07 on 2009-02-19
Thanks for the reply. Yes I can see USR8700 under network AND under Windows Workgroup. 

I tried draging it to the desktop but get an error message:

"operation not supported by backend"

Any ideas?

---

### Post by perrti-y02 on 2009-02-19
as a fairly simple way of creating a link you can use the ln command.

The works as follows

ln -s directorywhereyournetworkthingis home/yourusername/Desktop/nameoflinkyouwant

This should give a link (little picture of a folder with an arrow beside it) to the storage device. the -s means it creates a symbolic link which can be attached to a directory instead of just a file.

---

### Post by pasha07 on 2009-02-19
Thanks a bunch. I'll def try it. but does that autumatically mount the storage devices, if it's not mounted at startup?

---

### Post by perrti-y02 on 2009-02-19
as a fairly simple way of creating a link you can use the ln command.

The works as follows

ln -s directorywhereyournetworkthingis home/yourusername/Desktop/nameoflinkyouwant

This should give a link (little picture of a folder with an arrow beside it) to the storage device. the -s means it creates a symbolic link which can be attached to a directory instead of just a file.

---

### Post by perrti-y02 on 2009-02-19
accidently posted twice.

As far as I know it just creates a little link such that when you access it a window opens and it then mounts it. give it a go and see what it does.

---

