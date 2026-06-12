---
title: "sudo: pam_authenticate: Module is unknown"
date: 2006-07-08
forum: Desktop Environments
---

### Post by matko on 2006-07-08
hello i have veeeeeeery big problem. cant use sudo.
when i try i receive this

help me please

```
[SIZE="5"]matko@dapper:~$ sudo mount /dev/hda6
sudo: pam_authenticate: Module is unknown
matko@dapper:~$ sudo apt-get update
sudo: pam_authenticate: Module is unknown
matko@dapper:~$ su
su: Module is unknown
&#317;utujem.
matko@dapper:~$ /etc/sudoers
bash: /etc/sudoers: Permission denied
matko@dapper:~$ /etc/pam.d/sudo
bash: /etc/pam.d/sudo: Permission denied
matko@dapper:~$ sudo /etc/pam.d/sudo
sudo: pam_authenticate: Module is unknown
matko@dapper:~$[/SIZE]

```

---

