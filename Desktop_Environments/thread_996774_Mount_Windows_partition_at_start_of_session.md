---
title: "Mount Windows partition at start of session"
date: 2008-11-29
forum: Desktop Environments
---

### Post by rbaptista on 2008-11-29
I like how I can make Ubuntu (8.10) remember the user password so I don’t have to type it in every time I open my Windows XP partition. But isn’t there a way to mount the partition automatically at the start of the session, prefferably without requiring me to have to type the password again? I’ve seen similar threads around but they aren’t for the latest version of Ubuntu, so I was hesitant.

---

### Post by kellerfilip on 2008-11-29
I have put this line in /etc/fstab :
/dev/sda7       /d              vfat    user,uid=1001,gid=1000,iocharset=iso8859-2,codepage=1250,noexec,nosuid,nodev,umask=007        0       0

and it does what you are looking for (obviously you need to change uid and gid. I had to put this there because of the rw access)

---

### Post by taurus on 2008-11-29
If your XP uses ntfs filesystem, you can configure it to mount and write with ntfs-config.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

