---
title: "Help with &quot;You specified an invalid share name&quot; Error"
date: 2006-08-05
forum: Desktop Environments
---

### Post by mojohn on 2006-08-05
Hi. I've researched the forums and followed the directions at this link:

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Dapper#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

I am running Dapper and have the most current versions of samba and smbfs. 

I created a folder in /media called music to mount the network drive to. I have tried to mount a Windows network drive that contains my music collection. When I entered sudo mount smbfs -t //office/backup/music /media/music, I got the following error message: 

11104: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

If anyone could help with this issue, I would be most appreciative

John Miller

---

### Post by mojohn on 2006-08-08
One of my co-workers provided the solution. I was trying to mount a folder on a drive rather than the drive alone. When I changed the instruction to:

mount -t smbfs //office/backup /media/music,

things worked like they're supposed to.

John

---

