---
title: "can't download files with firefox"
date: 2009-01-31
forum: General Help
---

### Post by yanivgo on 2009-01-31
Hi all
just installed ubuntu for the first time (been windows user since ever)
i played around with it and I must say I'm having fun though I had some problems 
anyway my major problem which I cant fix is that from some reason I cant download any files with firefox sometimes I get the dialogue asking me if I want to open or save the file if I choose to save it just disappear but no file is being saved or downloaded and sometimes I don't get it at all
any suggestions?

---

### Post by taurus on 2009-01-31
From firefox, look in Edit -> Preferences -> Main and see where all your downloads go.  You can either set it to download automatically or ask you first.

---

### Post by ugm6hr on 2009-01-31
> **taurus said:**
> From firefox, look in Edit -> Preferences -> Main and see where all your downloads go.  You can either set it to download automatically or ask you first.

You can also ask it to show the downloads window.

If you download a lot, I would suggest the downthemall plugin:
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

---

### Post by yanivgo on 2009-01-31
> **taurus said:**
> From firefox, look in Edit -> Preferences -> Main and see where all your downloads go.  You can either set it to download automatically or ask you first.
 thanks taurus for replying so fast
 but the problem isn't the location of the file they just wont download at all!! (I know where they supposed to be saved) I just cant get it to download

more ideas are mostly welcome

---

### Post by taurus on 2009-01-31
What are you trying to download?  Can you give a specific link as an example?

---

### Post by ugm6hr on 2009-01-31
> **yanivgo said:**
> more ideas are mostly welcome

Are you trying to download somewhere other than /home/username?

If so try again into that directory (e.g. Documents).

It may be that you are trying to download to a directory you do not have automatic permission to write to.

---

### Post by yanivgo on 2009-01-31
OK so now we made a progress :D
yes I'm trying to download to other directory and yes when i changed it back to /home/username it's working!!
so now can someone tell me how to get the permission to write to other folder/partions on my hdd?

thanks

---

### Post by taurus on 2009-01-31
Applications -> Accessories -> Terminal
```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ugm6hr on 2009-01-31
Most directories have restricted permissions for a reason.

As taurus explained - you can copy & paste into anywhere using gksudo nautilus.

If you want to download directly from Firefox - you will have to set the ownership permissions as different than default.  Where would you like to be able to download to?

---

### Post by yanivgo on 2009-01-31
my hd have three partitions
1 windows xp
2 ubuntu linux
3 docs and files
i want to be able to download directly to my docs and files partitions

thanks again

---

### Post by ugm6hr on 2009-01-31
Is that partition ntfs, fat, or ext?

If you don't know:
```
sudo fdisk -l
```

---

### Post by yanivgo on 2009-01-31
> **ugm6hr said:**
> Is that partition ntfs, fat, or ext?

If you don't know:
```
sudo fdisk -l
```

it's ntfs

---

### Post by albinootje on 2009-01-31
> **yanivgo said:**
> it's ntfs

Please post the output of :
```

id
cat /etc/fstab

```

---

### Post by ugm6hr on 2009-01-31
> **yanivgo said:**
> it's ntfs

The simplest method is to install [ntfs-config]("apt:ntfs-config")

It adds a menu entry for NTFS configuration which is pretty self explanatory.  From memory, it allows you read/write access to the mountpoint.

---

### Post by yanivgo on 2009-02-01
ntfs-config works like a charm
thanks all

---

