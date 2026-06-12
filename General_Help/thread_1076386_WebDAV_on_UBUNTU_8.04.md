---
title: "WebDAV on UBUNTU 8.04"
date: 2009-02-21
forum: General Help
---

### Post by mortamus on 2009-02-21
Is WebDAV really supposed to run under Hardy? I set it up according to instructions found in this forum, but DAV does not appear to actually be running. If anyone is successfully running WebDAV (DAV/2) I'd love to hear from you.

Here's my config file:

```
## Directory of the DavLock file
DavLockDB /usr/share/apache2/var/DavLock
       
## Set up the myWebDAV directory to use WebDAV and authentication
<Directory /var/www/WebDAV>
       	Dav On
        AuthName DAV
        AuthType Basic
        AuthUserFile /etc/apache2/.htpasswd
        require user me
        Order allow,deny
        Allow from all
</Directory>

```

Also I have ,htaccess setup on the WebDAV directory and it does do the logon bit and display the folder contents. I have verified the lock database, Index and MultiView options, and the file/directoy ownership and permissions. Of course I have enabled dav and dav_fs and Apache reports that it is running DAV/2. What else can I check/do?

---

### Post by leachyboy2001 on 2009-03-24
Here is the tutorial I used, it seems to be working correctly, as far as I can tell
[http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10]("http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10")

---

