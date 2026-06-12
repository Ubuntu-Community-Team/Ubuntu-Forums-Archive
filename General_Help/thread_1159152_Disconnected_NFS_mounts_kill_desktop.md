---
title: "Disconnected NFS mounts kill desktop"
date: 2009-05-14
forum: General Help
---

### Post by johnnybirdman on 2009-05-14
I'm having a problem where my NFS mounts (from a freenas box) when the freenas box is disconnected/off kills my desktop.  I can't open home, can ls in a termianl (local or ssh) without a reboot.  Anyone else notice this or have a similar problem.  I mount the NFS shares in /etc/fstab with the command below (changed to protect the guilty)...
```
"FREENAS IP":/mnt/media /home/user/media nfs size=8192,wsize=8192,timeo=14,intr
```

I'm not sure that it matters but the freenas box is a virtual machine on the same box as the desktop I'm talking about.  It does pose a problem since the freenas doesn't load until after the desktop of the shares seem to automount when freenas comes up okay, it's when freenas goes down that I have problems..??
Any ideas would be great.
Thanks,
J.

---

### Post by highgeere on 2009-05-21
I'll bump this. I've noticed the same issue with NFS mounts between my ubuntu machines. If I reboot or shut down the box that hosts the NFS shares, all filesystem access is lost to nautilus on the other box. If I open a terminal I still have complete access, but nautilus just hangs. Also, if I issue 'df' the output hangs after it lists the local filesystems. I am not able to break out of that at all. I haven't found any decent output in dmesg or elsewhere. Any thoughts?

---

