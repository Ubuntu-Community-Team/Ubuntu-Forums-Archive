---
title: "VSFTPD - 530 Login Incorrect Error"
date: 2009-04-26
forum: General Help
---

### Post by LiQuidAiR on 2009-04-26
I haven't been able to figure out how to get VSFTPD to work.  I think I've narrowed it down to a Pam problem. But, I cannot confirm that.  I don't know how.

I basically have a simple setup with Virtual Users.  Below is my vsftpd.conf file -

listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
local_umask=022
anon_upload_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
chroot_local_user=YES
chroot_list_enable=NO
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key


ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
guest_enable=YES
guest_username=vftpuser
user_config_dir=/etc/vsftpd/vusers

force_dot_files=YES
#hide_ids=YES
max_per_ip=2
max_clients=20


I even went and found the libdb3 files and installed those thinking it could be a version error.  I thought this because the author from of VSFTPD said he used version 3 and most HOWTO's are written with version 3 as the program type.


I created the login file as specified by [ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.5/EXAMPLE/VIRTUAL_USERS/README](ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.5/EXAMPLE/VIRTUAL_USERS/README). 

My vsftpd.pam is as follows - 

auth required /lib/security/pam_userdb.so db=/etc/vsftpd_login
account required /bin/security/pam_userdb.so db=/etc/vsftpd_login

When I log in using FileZilla from outside my network I get a login incorrect error.  I haven't tried to add passive mode to the vsftpd.conf file and switch that on within my firewall.  I'll do that now. 

Has anyone else had this problem?

---

### Post by LiQuidAiR on 2009-04-27
Any takers?

---

### Post by LiQuidAiR on 2009-04-28
I figured it out!

Well, a little known fact about using a user name within your "login.txt" file that is already a user name within your local /etc/passwd file just doesn't work.  Well, it works but you have to specify the password for the local user not the one you created within login.txt.

I only figured this out after I started reading the vsftpd man page.
[http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)

I figured I would start from ground zero since no one knew how to solve the issue and read over a paragraph about local users and anonymous users and figured it out.

---

