---
title: "help with XAMPP settings"
date: 2008-09-05
forum: Desktop Environments
---

### Post by Ascenti0n on 2008-09-05
Hi all,

I'm in the middle of trying to setup a LAMP environment using XAMPP, to develop web apps and Drupal. I downloaded and installed XAMPP easily enough on my Hardy desktop, installed to '/opt'.

Problems came when when trying to import a MySQL dump from windows XP. The file size is: 11.4 mg. When I did this through Phpmyadmin it through up file size errors. I searched the forums and Google following advicxe and making changes as the errors came up.

This post is just to ask if the changes I have made are OK, despite no more errors, and as you know just because you are not getting an error msg, it doesn't mean I've setup my environment correctly. Here are the lines within the files I've changed:

***********************
 /opt/lampp/etc/my.cnf
***********************
# The MySQL server
[mysqld]
port		= 3306
socket		= /opt/lampp/var/mysql/mysql.sock
skip-locking
key_buffer = 150M
max_allowed_packet = 5M
table_cache = 200
sort_buffer_size = 2M
net_buffer_length = 8K
read_buffer_size = 2M
read_rnd_buffer_size = 512K
myisam_sort_buffer_size = 8M



***********************
 /opt/lampp/etc/php.ini
***********************
; Maximum allowed size for uploaded files.
upload_max_filesize = 100M


If anyone has configured XAMPP on their own system, does this look right?

---

