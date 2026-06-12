---
title: "HOWTO: Mount an NTFS drive on start up"
date: 2005-06-20
forum: Desktop Environments
---

### Post by RichZA on 2005-06-20
Hey

As far as I understand I need to edit the /etc/fstab file which I have done, and it is mounted. However only root has access to the drive. How do I configure it so that my normal account can access the drive?

Thanx in advance,
Rich

---

### Post by afonic on 2005-06-20
Just chown -R user:group the mounted dir.

---

### Post by YaAqoB on 2005-06-20
[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Hope this helps   :smile:

---

### Post by RichZA on 2005-06-20
Thanks :-)

---

