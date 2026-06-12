---
title: "Correct user permissions for apache2 and vsftpd"
date: 2009-05-15
forum: General Help
---

### Post by techno_kid on 2009-05-15
[B]i found the below quote in an old thread and it didn't have an answer to it. i had a play around and it seemed that the problem was the user that the ftp server ran under. if you change it to a local user and the site folder owner to that local user you would find it worked perfectly using ftp. am i correct here or am i going mad?

note: the problem only occurs when trying to add files via ftp.
[/B]             
                                                                > 
ok so I have apache running vhosts and vsftpd installed for ftp access. Folder structure as follows:

/home/www-domain-com/public_html/
/home/www-domain-com/logs/

/home/www-domain2-com/public_html/
/home/www-domain2-com/logs/

The vhost configs point directly to the user home folders' public_html and logs folders.

The problem I am encountering now is one of permissions. If I create the public_html/logs folders with sudo mkdir they're owned by root and the web server serves the vhost files fine, but the users can't do anything with ftp.

If the folders are owned by the user, apache appears to not be able to read the files/ignores them completely with the usual "You do not have permission to ..." However in this configuration the ftp clearly works fine.

I have tried adding the users supplemental group to www-data and then chown the public_html folders to www-data but that didn't seem to help much.


---

