---
title: "Red x over all document icons in home folder after mounting of NFS shares"
date: 2015-05-05
forum: Desktop Environments
---

### Post by Bjrnar_Lingjerde on 2015-05-05
Hi
After reinstalling ubuntu 14.04 and re-mounting my Synology NAS shared folder through adding these lines in /etc/fstab, all my icons in the home folder has a red cross over them including the mounted folders and all the files in the mounted folders. Is this an permission issue or another bug?
I am not sure how I mounted these folders before the reinstall.

# automount folders synology
#192.168.10.121:/volume1/video /home/b/NASVideo nfs nouser,atime,auto,rw,dev,exec,nosuid 0 0
#192.168.10.121:/volume1/photo /home/b/NASBilder nfs nouser,atime,auto,rw,dev,exec,nosuid 0 0
#192.168.10.121:/volume1/Data /home/b/NASData nfs nouser,atime,auto,rw,dev,exec,nosuid 0 0
#192.168.10.121:/volume1/music /home/b/NASMusikk nfs nouser,atime,auto,rw,dev,exec,nosuid 0 0

a "ls -l" of the home folder looks like this:
drwxrwxr-x 12 b      b       4096 mai    5 20:37 Cloud Station
drwxrwxrwx 16 nobody nogroup 4096 april 14 09:52 NASBilder
drwxrwxrwx 14 nobody nogroup 4096 mai    5 16:11 NASData
drwxrwxrwx 11 nobody nogroup 4096 mars  28 18:59 NASMusikk
drwxrwxrwx 10 nobody nogroup 4096 april 13 11:13 NASVideo
drwxr-xr-x  2 b      b       4096 mai    5 17:51 Nedlastinger
drwxr-xr-x  2 b      b       4096 mai    5 20:35 Skrivebord

I am really blind here, can anyone help?

---

