---
title: "VSFTPD virtual user problem"
date: 2009-03-14
forum: General Help
---

### Post by artheus on 2009-03-14
Hey!

I've set up virtual users in my VSFTPD. And the login is working as it should..
But when I use the chroot_local_user=YES, the user get sent to the secure_chroot_dir ("jail") and the user can't make any directories or upload any files. Even if write_enable=YES.
What can I do to chroot the virtual user to the assigned folder, without the problem that the user is being sent to "jail"?

my vsftpd.conf (without chroot_local_user) :

```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_std_format=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```

This is working.. But now the virtual users have access to every single folder and file on the server.. Wich is not so great..

Cheers,
Artheus

---

### Post by artheus on 2009-03-14
I solved this myself! :)

It was the privileges of the folder.. A minor mistake..

---

