---
title: "Mount NFS Fedora server to Ubuntu laptop"
date: 2009-03-24
forum: General Help
---

### Post by lordsvae on 2009-03-24
Hi. I'm new to this forum as this is my first post. So sorry if I post in the wrong section and not doing this correctly, but here we go.

I've installed a Fedora version 9 server, and had it running for over a year now, but never got the Linux to Linux shareing working. Sharing folders to a windows xp PC works all fine, but when I try to mount a simple folder from Fedora server to an Ubuntu laptop I get this error message after running "sudo mount -a":
```
mount.nfs: internal error
```

Now I've searched this forum and some others, but couldn't find a clear sollution to the problem, or trying stuff out myself.

This is my servers /etc/exports:
```
/Shared 10.0.0.0/255.255.255.0(rw,sync)
```
after I run "exportfs -a", this is whats in /var/lib/nfs/etab
```
/Shared 10.0.0.0/255.255.255.0(rw,sync,wdelay,hide,nocrossmnt,secure,root_squash,no_all_squash,no_subtree_check,secure_locks,acl,anonuid=65534,anongid=65534)
```
Now, from what I know, that should share the folder to anyone on the local network with read-wright.

Server user info:
```
torsva:x:500:500:My Name:/home/torsva:/bin/bash
```
Laptop user info:
```
torsva:x:1000:1000:My Name:/home/torsva:/bin/bash
```

My laptops /etc/fstab:
```
10.0.0.3:/Shared /home/torsva/Skrivebord/server/Shared nfs defaults 0 0
```

Just in general, what am I doing wrong?
Can it be that I'm trying to mount from Fedora to Ubuntu?
Cause I've done this exact same thing from Fedora to Fedora and then it worked. From what I can see, the only thing thats different is the usergroup and userid on the laptop.
As you can immagine, I'm only speculating here.

Cheers for the help and I hope I get this solved
LordSvae

---

### Post by Iowan on 2009-03-24
A couple of help pages for you to check:
[https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html]("https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html")
[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

### Post by gamewolf on 2009-03-24
Quick question: How did you get XP to mount a NFS share?

---

### Post by lordsvae on 2009-03-26
> **gamewolf said:**
> Quick question: How did you get XP to mount a NFS share?

I didn't. I used Samba for that.

---

### Post by lordsvae on 2009-03-26
> **Iowan said:**
> A couple of help pages for you to check:
[https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html]("https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html")
[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

Thanks, I'll check those out first thing. As of now I'm using SSHFS, tho I turn into some problems there, which are common. Like you can't drag files to that mount, it states that there is no free space on it, and I can't find a post where it has been solved yet. The good thing about SSHFS is that I can mount this when I'm not even in my hous. It through SSH(port nr 22) which I have allready set up for my server.

But I'd really want to get NFS sharing to work still. So I'll get those posts checked out.

Thanks
LordSvae

---

