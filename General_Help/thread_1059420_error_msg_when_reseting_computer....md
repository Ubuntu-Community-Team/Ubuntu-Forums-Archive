---
title: "error msg when reseting computer..."
date: 2009-02-03
forum: General Help
---

### Post by Mia_tech on 2009-02-03
when I reset my pc, while is shooting down I get error:

```
CIFS VFS: SERVER NOT RESPONDING
```

I'm suspecting something with the way the remote share is mounted

here's what I'm using to mount the share on my fstab file

```
//192.168.10.3/winshare	/media/winshare	cifs	credentials=/root/.smbcredentials,dir_mode=0777,file_mode=0777	0	0
```

any help appreciated

---

### Post by jimv on 2009-02-03
Can you access the share by typing smb://192.168.10.3/winshare in Nautilus?

---

### Post by Mia_tech on 2009-02-04
no, I can't, this is what I got

```
Could not find "//10.200.50.7/winshare".
```

---

