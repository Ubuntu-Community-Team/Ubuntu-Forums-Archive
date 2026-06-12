---
title: "Permanent Drive Connection to NAS"
date: 2009-09-16
forum: Desktop Environments
---

### Post by SnellC on 2009-09-16
Please help, i cant seem to get the right command line in fstab to map network drive that actually makes use of the credentials supplied, as once mapped it tells me i dont have permissions.

Heres the command line im using. Strange thing is if i do a mount or smb mount or mount using the ubuntu gui, i can see the files on the NAS, just not after using fstab. Im certain using fstab is using root permissions and ignoring the crds ive supplied which is why it tells me i dont have permissions to see the content of the NAS.

//192.168.1.100/root /home/MyUsername/n4100plus cifs username=MyUsername,password=MyPassword

Thanks

---

