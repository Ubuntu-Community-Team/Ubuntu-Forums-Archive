---
title: "vsftpd does not create its own directory"
date: 2022-02-16
forum: Desktop Environments
---

### Post by johnaaronrose on 2022-02-16
I noticed that when vsftpd is installed that no vsftpd (or similar name) directory is created in /etc. This also happens on Ubuntu, is this expected. The reason that I ask is that I've configured vsftpd and "sudo systemctl restart vsftpd" seems to to work but "sudo systemctl status vsftpd" shows that vsftpd failed with exit code 2 (invalid argument). Any ideas?

---

### Post by ActionParsnip on 2022-02-16
What is the output of:
```

lsb_release -a; uname -a; apt-cache policy vsftpd

```
Thanks

---

### Post by johnaaronrose on 2022-02-16
root@JohnNUC:/# lsb_release -a; uname -a; apt-cache policy vsftpd
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:    20.04
Codename:    focal
Linux JohnNUC 5.4.0-99-generic #112-Ubuntu SMP Thu Feb 3 13:50:55 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
vsftpd:
  Installed: 3.0.3-12
  Candidate: 3.0.3-12
  Version table:
 *** 3.0.3-12 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by #&amp;thj^% on 2022-02-16
Wouldn't hurt to see this as well:
```
cat /etc/vsftpd/vsftpd.conf
```
More information will help you get help.

---

### Post by Skaperen on 2022-02-16
i'm not using **[FONT=courier new]vsftpd[/FONT]** so this is no issue for me, but i noticed ...
```

lt2a/forums /home/forums 6> ls -dl /etc/vsftpd
/bin/ls: cannot access '/etc/vsftpd': No such file or directory
lt2a/forums /home/forums 7> 

```

---

### Post by johnaaronrose on 2022-02-16
Attached are all the relevant files in a tar.gz archive including the pam.d from /etc.
I'm trying to set up virtual users as per [https://docs.rockylinux.org/guides/file_sharing/secure_ftp_server_vsftpd/#virtualusers](https://docs.rockylinux.org/guides/file_sharing/secure_ftp_server_vsftpd/#virtualusers)
but with the difference that I don't want to use secureFTP but instead use ftps.
BTW I'm using Xununtu 20.04.3

---

### Post by johnaaronrose on 2022-02-17
Here is the Terminal output for vsftpd:
```
root@JohnNUC:~# systemctl start vsftpd
root@JohnNUC:~# systemctl status vsftpd
&#9679; vsftpd.service - vsftpd FTP server
     Loaded: loaded (/lib/systemd/system/vsftpd.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Thu 2022-02-17 06:50:16 GMT; 9s ago
    Process: 271172 ExecStartPre=/bin/mkdir -p /var/run/vsftpd/empty (code=exited, status=0/SUCCESS)
    Process: 271179 ExecStart=/usr/sbin/vsftpd /etc/vsftpd.conf (code=exited, status=2)
   Main PID: 271179 (code=exited, status=2)

Feb 17 06:50:16 RoseServer systemd[1]: Starting vsftpd FTP server...
Feb 17 06:50:16 RoseServer systemd[1]: Started vsftpd FTP server.
Feb 17 06:50:16 RoseServer systemd[1]: vsftpd.service: Main process exited, code=exited, status=2/INVALIDARGUMENT
Feb 17 06:50:16 RoseServer systemd[1]: vsftpd.service: Failed with result 'exit-code'.
```
In the attached tar.gz file the files are copied from /etc/ to a directory in my /home and I changed owner & group to me in that location.

---

