---
title: "NFS share over OpenVPN not mounting at boot, but does mount with &quot;mount -a&quot;"
date: 2008-12-25
forum: General Help
---

### Post by DinkyDogg on 2008-12-25
Since I upgraded from Hardy to Intrepid, my computer isn't mounting my NFS share on boot. I've got an OpenVPN set up, and the daemon runs properly. Here's the line from my fstab:
```
10.8.0.1:/var/nfs		/mnt/nfs/		nfs	rw
```

After I've booted, if I do "sudo mount -a", it mounts, but it doesn't mount automatically when I boot.

Any ideas why? Is there a log I should look at for more information?


Thanks.

---

