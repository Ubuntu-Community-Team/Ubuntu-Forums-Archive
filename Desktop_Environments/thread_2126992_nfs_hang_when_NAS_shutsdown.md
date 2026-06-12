---
title: "nfs hang when NAS shutsdown"
date: 2013-03-18
forum: Desktop Environments
---

### Post by Dusenberg on 2013-03-18
lubuntu 12.10, home wireless net environment, Synology NAS

I have a NAS drive that has a scheduled start/shutdown to roughly coincide when we are at home. The NAS holds photos and music, and generally just is used for reads.  My laptop automounts two shares on the NAS via nfs. 

Problem is that if the NAS shuts down while my laptop is running, file manager just hangs and I can't do any saves/open of local laptop files from any applications. Shutting the laptop down causes shutdown to hang.  Running 'mount' from terminal when the NAS box has shutdown shows the NAS mounts still there.  Running 'sudo umount [nas mount]' just hangs. 

I've read/re-read the nfs docs and googles, and thought I had it sussed, and have I've tried several things but can't solve this prob.  Does anyone know how can I make the nfs mounted shares unmount gracefully if/when the NAS 'dies'??

The nfs mount statement in fstab is:
DISKSTATION:/volume1/Photos /mnt/NAS_Photos nfs _netdev,intr,timeo=5,retrans=28,bg,rsize=8192,wsize=8192,atime,auto,rw,dev,exec,suid 0 0

'mount' reports:
DISKSTATION:/volume1/Photos on /mnt/NAS_Photos type nfs (rw,intr,timeo=5,retrans=28,bg,rsize=8192,wsize=8192,addr=192.168.1.3,_netdev)

Thanks

---

### Post by LewisTM on 2013-03-19
It would be nice to know what you tried so we don't waste our time suggesting the same thing.

You should keep the mount options to a minimum and see if that helps, then add them back one by one. You have many, some which may be redundant (i.e. already default), others which may interfere with proper unmounting. I'm thinking of the bg option which would fork a new mount process on each fail, never letting go.

Cheers!

---

### Post by Dusenberg on 2013-03-21
Thanks LewisTim - take your point, and don't want to waste anyone's time.

As I hadn't used nfs before, I googled the setup options from some other forum.  I have read up on them but I must admit to not really understanding them sufficiently. 

Your comment re bg makes a lot of sense, as does keeping things simple.  I've made some changes and removed 'intr,timeo=5,retrans=28,bg' and will post once results of tests.

Thanks

---

### Post by papibe on 2013-03-21
Hi Dusenberg.

This is what I do:

If nfs shares are on servers that are not 24/7, I don't use fixed mount points on the fstab. Instead, I use autofs (read about it [here]("https://help.ubuntu.com/community/Autofs")).

The default settings have a little better less freeze time that a fixed mount, but there's a way to get around it. If you use an indirect map that points to an executable script, you can have the opportunity to decide whether to mount the share if the server is up. You can use either 'ping' or 'map' to do that.

Let us know if you need more help with that.
Regards.

---

