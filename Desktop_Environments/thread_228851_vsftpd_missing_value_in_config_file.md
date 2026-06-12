---
title: "vsftpd: missing value in config file"
date: 2006-08-03
forum: Desktop Environments
---

### Post by jmirick on 2006-08-03
I have had vsftp running before on a different machine, no problems.  I have created a new machine and entered what I believe is a correct config file, but it won't connect, and when I try to start it via "vsftpd" at the shell it says,

500: vsftpd:  missing value in config file:

and that's all, folks.  What's missing??  I've looked at it for a few hours.

Firewall is off, nmap shows ports 20 & 21 not open (since I assume vsftpd isn't starting) so I'm stumped.

config file is:

[INDENT]
listen=YES
tcp_wrappers=yes

#     Allow anonymous FTP? (Beware - allowed by default if you comment this out).

anonymous_enable=no

#      The following enables users with a local account to log into FTP.  In this
#      current configuration, all FTP users must have a local account on this 
#      machine -- there is a way to do this without a local account, though.

local_enable=YES

#     When local users have logged in, jail them in their own home directory:

chroot_local_user=yes

write_enable=YES

#     Default umask for local users is 077. You may wish to change this to 022,
#     if your users expect that (022 is used by most other ftpds)

local_umask=022

#     Activate directory messages - messages given to remote users when they
#     go into a certain directory.

dirmessage_enable=YES
ftpd_banner=Welcome to the AMS Ubuntu2 FTP service

#     Make sure PORT transfer connections originate from port 20 (ftp-data):

connect_from_port_20=YES
 
#     Activate logging of uploads/downloads.

xferlog_enable=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES


#     Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.

#secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.

pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
[/INDENT]

---

