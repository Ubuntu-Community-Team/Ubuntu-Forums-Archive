---
title: "vsftpd parameters"
date: 2022-06-09
forum: Desktop Environments
---

### Post by johnaaronrose on 2022-06-09
I have installed the vsftpd ftp server. I want to be able to connect to a specific directory by specifying it in vsftpd conf parameters. Looking at [https://linuxize.com/post/how-to-setup-ftp-server-with-vsftpd-on-ubuntu-20-04/](https://linuxize.com/post/how-to-setup-ftp-server-with-vsftpd-on-ubuntu-20-04/) it says to use the following:
user_sub_token=$USER
local_root=/home/$USER/ftp

However, [http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html) does not list these parameters. Is there a web site that shows & explains all the parameters for the vsftpd conf file?

---

### Post by ActionParsnip on 2022-06-09
[https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-directory-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-directory-on-ubuntu-20-04)

DigitialOcean make great guides

---

