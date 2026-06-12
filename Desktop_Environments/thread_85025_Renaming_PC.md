---
title: "Renaming PC"
date: 2005-11-01
forum: Desktop Environments
---

### Post by Navyblue on 2005-11-01
I am not sure what is the right terminology to use. Ubuntu installation by default "name" the PC "ubuntu". How can I change this name after installation?

Thanks :)

---

### Post by l33tc0d34 on 2005-11-01
i can help u. from google:
[www.google.com](www.google.com)
sudo cat /dev/random > /etc/hostname

---

### Post by felix_stegerman on 2005-11-01
Edit /etc/hostname to change the hostname.

You should probably also replace the old name with the new one in /etc/hosts,
and if you've configured any servers (e.g. mail server) you might need to
replace the old name in the appropriate config files as well.


Felix

---

### Post by Navyblue on 2005-11-02
I tried changing the /etc/hostname (without the /etc/hosts though), it screwed up my su, sudo, kdesu and alike, and most of all it didn't work. So I've been wary of doing it. Would try that though.

Thanks. :)

---

### Post by Navyblue on 2005-11-02
Cool, my sudo works after a restart. Thanks All. :)

---

### Post by SickTwist on 2005-11-02
Also, this can be done from GNOME as well:

System --> Administration --> Networking

Click on the "General" tab and type the new hostname.

---

