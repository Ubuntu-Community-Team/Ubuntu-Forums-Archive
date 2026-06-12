---
title: "vsftpd setup correctly"
date: 2009-04-14
forum: General Help
---

### Post by jdcnosse on 2009-04-14
Okay, so I believe I have vsftpd setup correctly...but it's still not working...

I have created a user called ftp_user, and I have told vsftpd through the use of vsftpd.allowed_users and vsftpd.chroot_list that ftp_user is basically the only user to be allowed in.

I have opened up port 21 on my router too.

Here's what my vsftpd.conf file looks like.
```

# No anonymous login
anonymous_enable=NO
# Let local users login
# If you connect from the internet with local users, you should enable TLS/SSL/FTPS
local_enable=YES

# Write permissions
write_enable=YES

Just some users are "free":
chroot_local_user=YES
chroot_list_enable=YES
# Create the file /etc/vsftpd.chroot_list with a list of the "free" users.

# Allow only some users to login
userlist_deny=NO
userlist_enable=YES
userlist_file=/etc/vsftpd.allowed_users

# Enable encryption
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
# listen_port=990

```

---

### Post by Funkydonut5000 on 2009-04-15
Have you looked through this thread yet?

[FTP How to]("http://ubuntuforums.org/showthread.php?t=518293")

---

