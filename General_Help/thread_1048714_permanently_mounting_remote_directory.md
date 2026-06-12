---
title: "permanently mounting remote directory"
date: 2009-01-23
forum: General Help
---

### Post by tmetzcc325 on 2009-01-23
Hey all,

I have one PC that has all my music on it.  I have another PC on the same network from which I'd like to be able to play this music in Rhythmbox.  Ideally, I'd set the Rhythmbox library to look at the remote folder.

What is the best way to go about this?  I am familiar with Samba and the like, but am not really sure the proper way to have a remote directory be automatically mounted every time the PC without the music is rebooted.  I don't think I even need Samba, but that is where I am confused.

Any ideas?

Thanks,
Tom

---

### Post by albinootje on 2009-01-23
> **tmetzcc325 said:**
> Hey all,

I have one PC that has all my music on it.  I have another PC on the same network from which I'd like to be able to play this music in Rhythmbox.  Ideally, I'd set the Rhythmbox library to look at the remote folder.

What is the best way to go about this?
Both Linux machines ? If so, then NFS could be easier.
If not, check this :
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
--> start reading there :
```

Now create a directory where you want to mount your share (e.g. /media/samba_share):

sudo mkdir /media/samba_share

Now, using any editor, and add a line to /etc/fstab for your SMB share as follows:
--- cut for brevity ---

```

---

### Post by tmetzcc325 on 2009-01-23
Sorry, yes they are both Ubuntu Ibex machines.  I thought I had written that out, but apparently not :).

I don't think I need Samba for this, but am not experienced enough to know how to do this without it.

Any suggestions?

---

### Post by albinootje on 2009-01-23
> **tmetzcc325 said:**
> Sorry, yes they are both Ubuntu Ibex machines.  I thought I had written that out, but apparently not :).

I don't think I need Samba for this, but am not experienced enough to know how to do this without it.

Any suggestions?

As an example, for NFS would be like this :

On the machine with music, 192.168.1.2, where the music is in /music
```

sudo apt-get install nfs-kernel-server portmap
sudo su
echo "/music 192.168.1.0/255.255.255.0(rw,sync,subtree_check)" >> /etc/exports
/etc/init.d/nfs-kernel-server restart
exit

```

On the machine without music, 192.168.1.3 :
```

sudo apt-get install portmap nfs-common
sudo mkdir /media/test
sudo mount 192.168.1.2:/music /media/test -t nfs

```

---

