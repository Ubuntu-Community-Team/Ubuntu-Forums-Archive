---
title: "Issues with vsftpd"
date: 2017-10-23
forum: Desktop Environments
---

### Post by pingaan on 2017-10-23
Hi,

A week ago my FTP worked fine, both the private and the public part. Now a week later, for no reason (seemingly) the public part stopped working.

Here's my config:
```
listen=NOlisten_ipv6=YES
anonymous_enable=YES
anon_root=/media/pi/FTP/Public/
local_enable=YES
write_enable=YES
local_umask=022
chroot_local_user=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO
user_sub_token=pi
local_root=/media/pi/FTP/
allow_writeable_chroot=YES

```

When trying to access the public area it simply asks for the login info and when entered the browsing starts in /media/pi/FTP/. For some reason it seems as if it ignores "anonymous_enable=YES" and" anon_root=/media/pi/FTP/Public/".

Anyone who might be able to help?

Regards.

---

