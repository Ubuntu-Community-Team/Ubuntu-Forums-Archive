---
title: "sftp &amp; sudo"
date: 2006-10-01
forum: Desktop Environments
---

### Post by McHenry on 2006-10-01
I need to copy a fine from a server

I use sftp admin@192.168.1.1 to login in and enter the password when prompted.

To copy the file I need root privelidges however I cannot sftp root@192.168.1.1

So the question is once I sftp as admin how can I then sudo to root ?

Thanks

---

### Post by skymt on 2006-10-01
```
sudo -s
```

---

### Post by Mr Frosti on 2006-10-01
I really wouldn't recommend connecting to anything as root. The ideal setup would be for the server you are connecting to to have the permissions for the file changed so  that your user can access it using SFTP. A couple alternate ways are listed below:

If SFTP is running, so should SSH and SCP. You can "ssh [email]admin@ip.addr[/email]ess" and then sudo once you are logged in. You can change the file permissions this way and use SFTP.

You can also SCP by running "scp admin@remote_path local_path"

---

