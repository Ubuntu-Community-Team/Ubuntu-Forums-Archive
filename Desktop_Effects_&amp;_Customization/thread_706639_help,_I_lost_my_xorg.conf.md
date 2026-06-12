---
title: "help, I lost my xorg.conf"
date: 2008-02-24
forum: Desktop Effects &amp; Customization
---

### Post by AFeuer on 2008-02-24
while trying to follow a guide on how to enable dual monitors with an ati card I somehow lost my xorg.conf file.  I thought I made a backup but that is blank too.  I have no idea what happened, but I'm sure you can guess what my desktop environment is like...  What should I do?

---

### Post by Toadmund on 2008-02-24
Try this in your terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by AFeuer on 2008-02-24
here is what happened

```
adam@adam-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for adam:
md5sum: /etc/X11/xorg.conf: No such file or directory
adam@adam-desktop:~$ 


```

---

### Post by Toadmund on 2008-02-24
Your answer may be in  Mike D's 2nd post here:
[https://answers.launchpad.net/ubuntu/+question/4273]("https://answers.launchpad.net/ubuntu/+question/4273")

Good luck.

---

### Post by AFeuer on 2008-02-24
ok, i fixed it.  It seems that I must have copied a blank file over my backup.  I found another backup and used that one.  That link did help, thanks.

Adam

---

