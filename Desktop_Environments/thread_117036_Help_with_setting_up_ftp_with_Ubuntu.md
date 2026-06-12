---
title: "Help with setting up ftp with Ubuntu"
date: 2006-01-14
forum: Desktop Environments
---

### Post by edeboer68 on 2006-01-14
Anyone set up an ftp site using Ubuntu yet? Please help with any advice and links to whatever software that might be out there to help. 

Thanks  E

---

### Post by adwait on 2006-01-14
Download and install vsftp with
```
sudo apt-get install vsftp
```

Run vsftp with
```
sudo /etc/init.d/vsftpd start
```

The configuration file is at /etc/vsftpd.conf

---

