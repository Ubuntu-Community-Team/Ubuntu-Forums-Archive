---
title: "Only first mounted volume (by server) appears on Desktop/Places"
date: 2008-07-04
forum: Desktop Environments
---

### Post by LanceRushing on 2008-07-04
When I mount more than one volume from the same server, only the first mounted volume appears on the Desktop/Places.

Example:
```

mount -t smbfs -o username=user,password=pass //serverName/pictures /media/PictureDrive
mount -t smbfs -o username=user,password=pass //serverName/lance /media/LanceDrive

```

Only "PictureDrive" appears on the Desktop.

I figured out if I use the IP address for the second mount both will appear.
```

mount -t smbfs -o username=user,password=pass //serverName/m /media/MediaDrive
mount -t smbfs -o username=user,password=pass //10.0.0.2/lance /media/LanceDrive

```

However, I have 4 mounts and would like all of the mounted volumes to appear.

Is this a bug?? Or is there a setting somewhere (gconf?) that will show *all* volumes mounted even if they are from the same server? 

Thanks,
-Lance

---

