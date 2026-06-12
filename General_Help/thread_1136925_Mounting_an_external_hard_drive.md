---
title: "Mounting an external hard drive"
date: 2009-04-25
forum: General Help
---

### Post by pylon42 on 2009-04-25
Is it possible to have Ubuntu mount external hard drives as a user instead of root?

I'm trying to share the contents via Samba, but I can't since it mounts to /media/drive as root by default.

Any help would be appreciated.

---

### Post by kpkeerthi on 2009-04-25
Yes. You need to customize /etc/fstab
```

# Samba
//server/share  /media/samba  cifs  user=user,uid=1000,gid=100  0  0
# "Server" = Samba server (by IP or name if you have an entry for the server in your hosts file
# "share" = name of the shared directory
# "user" = your samba user
# This set up will ask for a password when mounting the samba share. If you do not want to enter a password, use a credentials file.
# replace "user=user" with "credentials=/etc/samba/credentials" In the credentials file put two lines
# username=user
# password=password
# make the file owned by root and ro by root (sudo chown root.root /etc/samba/credentials && sudo chmod 400 /etc/samba/credentials)

```

[https://help.ubuntu.com/community/Fstab#Examples]("https://help.ubuntu.com/community/Fstab#Examples")

---

