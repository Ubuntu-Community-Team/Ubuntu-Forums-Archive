---
title: "unable to change file permissions"
date: 2009-03-25
forum: General Help
---

### Post by karatekid on 2009-03-25
i want to change the file permissions for some particular files in a folder. i change it using chmod and it shows a successful change. However the  permissions are still not changed.

```

nitesh@nitesh-desktop:~$ sudo chmod -c 777 "/media/data/Nitesh/web designing/htdocs/index.php"
mode of `/media/data/Nitesh/web designing/htdocs/index.php' changed to 0777 (rwxrwxrwx)


```

this is the  details of the folder whose file permissions i want to change
```

nitesh@nitesh-desktop:/media/data/Nitesh/web designing/htdocs$ ls -ldh *
-rw-r-----  1 nitesh root 100K 2008-06-10 00:00 15.jpg
-rw-r-----  1 nitesh root 5.1K 2005-08-30 15:12 3col_rightNav.css
-rw-r-----  1 nitesh root  984 2008-07-26 16:05 accesscontrol.php
-rw-r-----  1 nitesh root 1.3K 2008-06-07 13:19 ajax.html
-rw-r-----  1 nitesh root 3.2K 2008-12-10 23:22 ajax-loader.gif
-rw-r-----  1 nitesh root 2.4K 2008-07-25 20:00 comments_add.php
-rw-r-----  1 nitesh root    0 2008-08-03 18:16 comments.css
-rw-r-----  1 nitesh root 4.8K 2008-08-03 18:17 comments.php
-rw-r-----  1 nitesh root 1.4K 2008-08-06 22:46 cprog.php
-rw-r-----  1 nitesh root 4.2K 2008-08-06 23:11 create_gall_album_ajax.php
-rw-r-----  1 nitesh root 2.9K 2008-06-30 00:36 create_gall_album_php.php
-rw-r-----  1 nitesh root 5.6K 2008-08-06 23:11 create_gall_photo_ajax.php
-rw-r-----  1 nitesh root 6.1K 2008-07-02 12:45 create_gall_photo_php.php
-rw-r-----  1 nitesh root 1.2K 2008-08-06 23:11 create_gall.php
-rw-r-----  1 nitesh root  452 2008-04-02 23:22 create_thumb.php
drwxr-x---  5 nitesh root  16K 2008-10-07 00:17 csi
-rw-r-----  1 nitesh root  28K 2008-10-12 01:51 csi.csv
drwxr-x---  2 nitesh root  16K 2009-01-10 17:30 css
-rw-r-----  1 nitesh root  543 2008-10-12 01:16 csv_process.php
-rw-r-----  1 nitesh root  693 2008-12-26 23:35 curr_page.php
-rw-r-----  1 nitesh root  163 2008-06-06 12:58 db_login_details.php
-rw-r-----  1 nitesh root  106 2008-04-16 23:08 db_login.php
-rw-r-----  1 nitesh root 104K 2008-10-12 01:02 db.xls
drwxr-x--- 36 nitesh root  16K 2008-07-31 21:10 dce
drwxr-x---  7 nitesh root  16K 2008-12-26 21:10 dce_links
-rw-r-----  1 nitesh root 6.1K 2008-08-04 23:30 dceupdates.html
-rw-r-----  1 nitesh root  582 2008-07-30 00:50 download.css
-rw-r-----  1 nitesh root 2.8K 2008-07-29 23:57 download.php
drwxr-x---  3 nitesh root  16K 2008-08-22 21:01 eindia
drwxr-x---  6 nitesh root  16K 2009-01-23 21:15 esummit
drwxr-x---  2 nitesh root  16K 2008-06-16 22:11 external
-rw-r-----  1 nitesh root  964 2008-08-01 22:40 favicon.ico
-rw-r-----  1 nitesh root  964 2008-08-01 22:40 favicon.jpg
-rw-r-----  1 nitesh root 5.2K 2008-10-06 22:00 file_manager_ajax.php
-rw-r-----  1 nitesh root 4.5K 2008-06-20 00:15 file_manager_php.php
drwxr-x---  4 nitesh root  16K 2008-03-29 19:23 gallery
-rw-r-----  1 nitesh root 1.5K 2008-07-31 00:51 gallery.css
-rw-r-----  1 nitesh root 3.9K 2008-07-31 00:45 gallery.php
-rw-r-----  1 nitesh root 1.2K 2008-03-31 23:54 gall.php
-rw-r-----  1 nitesh root  833 2008-06-21 22:00 get-post.php
-rw-r-----  1 nitesh root  798 2008-08-03 01:00 head.css
-rw-r-----  1 nitesh root 3.3K 2008-07-26 19:30 http header no_access.html
drwxr-x---  3 nitesh root  16K 2008-03-09 17:12 images
[COLOR="Red"]-rw-r-----  1 nitesh root 1.8K 2008-08-03 13:27 index.php[/COLOR]
drwxr-x---  2 nitesh root  16K 2009-01-10 17:30 js
-rw-r-----  1 nitesh root 1.7K 2008-12-12 22:13 layout.css
-rw-r-----  1 nitesh root 1.4K 2008-12-11 22:01 loading.html
-rw-r-----  1 nitesh root 5.5K 2008-12-11 22:57 loading.php
-rw-r-----  1 nitesh root 6.1K 2009-01-27 01:05 login.js
-rw-r-----  1 nitesh root 4.3K 2008-07-27 13:46 login.php
-rw-r-----  1 nitesh root 1011 2008-07-24 23:59 logout.php
-rw-r-----  1 nitesh root 1.7K 2008-08-03 22:32 menu.css
drwxr-x---  2 nitesh root  16K 2009-01-10 17:30 menufiles
drwxr-x---  2 nitesh root  16K 2008-03-19 21:49 misc
drwxr-x--- 10 nitesh root  16K 2008-03-07 21:52 MyAdmin
-rw-r-----  1 nitesh root  29K 2008-01-21 18:34 mypic.jpg
-rw-r-----  1 nitesh root 2.3K 2008-08-06 22:57 navigation.php
drwxr-x---  2 nitesh root  16K 2009-01-15 22:20 New Folder
-rw-r-----  1 nitesh root 1.4K 2008-07-26 16:23 no_access.html
-rw-r-----  1 nitesh root 1.3K 2008-07-26 19:31 no_access.php
drwxr-x---  2 nitesh root  16K 2008-03-13 16:43 _notes
-rw-r-----  1 nitesh root 1.9K 2009-03-17 17:46 perc.php
drwxr-x---  8 nitesh root  16K 2008-12-11 21:43 phoenix
-rw-r-----  1 nitesh root 125K 2009-01-01 10:57 phoenix.exe
-rw-r-----  1 nitesh root  74K 2009-01-01 10:56 phoenix.rar
-rw-r-----  1 nitesh root   19 2008-02-28 16:41 phpinfo.php
-rw-r-----  1 nitesh root  24K 2007-12-27 22:51 pict_gall.php
-rw-r-----  1 nitesh root 1.4K 2008-08-06 22:46 politics.php
-rw-r-----  1 nitesh root  140 2008-07-24 14:27 post2.php
-rw-r-----  1 nitesh root 1.8K 2008-07-26 19:34 post_request.php
-rw-r-----  1 nitesh root 3.3K 2008-10-06 21:52 process_upload.php
-rw-r-----  1 nitesh root 1.1K 2008-06-24 00:25 profile.php
-rw-r-----  1 nitesh root  117 2008-08-03 22:19 quotes.css
-rw-r-----  1 nitesh root 2.5K 2008-07-30 22:35 quotes.php
-rw-r-----  1 nitesh root  832 2008-08-07 21:50 reading.css
-rw-r-----  1 nitesh root 1.1K 2008-08-06 21:31 reading.php
-rw-r-----  1 nitesh root  770 2008-07-30 01:01 register.css
-rw-r-----  1 nitesh root 4.8K 2008-07-27 12:58 register.php
-rw-r-----  1 nitesh root 3.5K 2009-03-25 19:44 shell_process_upload.php
-rw-r-----  1 nitesh root 1.9K 2009-03-25 19:42 shell_upload.php
-rw-r-----  1 nitesh root  27K 2008-08-20 18:35 sixpc.php
-rw-r-----  1 nitesh root  970 2008-08-06 21:45 source_link.php
drwxr-x---  2 nitesh root  16K 2008-08-21 22:00 stf
-rw-r-----  1 nitesh root 7.4K 2008-06-05 01:06 stu_nicoll.html
-rw-r-----  1 nitesh root 1.3K 2008-08-06 22:32 tech.php
-rw-r-----  1 nitesh root 1.2K 2008-03-27 23:23 thumb.php
-rw-r-----  1 nitesh root  89K 2008-06-10 00:07 Thumbs.db
-rw-r-----  1 nitesh root 4.0K 2009-01-28 20:33 update.js
-rw-r-----  1 nitesh root 3.3K 2008-07-25 18:07 upload2.php
-rw-r-----  1 nitesh root  341 2008-07-29 23:48 upload.css
-rw-r-----  1 nitesh root 3.3K 2008-07-29 23:49 upload.php
-rw-r-----  1 nitesh root 1.1K 2008-08-06 23:05 user_status.php
-rw-r-----  1 nitesh root 3.5K 2008-08-09 14:06 webdev.php
drwxr-x---  6 nitesh root  16K 2008-10-15 22:45 xampp
drwxr-x---  5 nitesh root  16K 2009-01-10 17:30 yui


```

---

### Post by kanikilu on 2009-03-25
What filesystem does /media/data have? If it's not a linux native format (such as ext2, ext3...) and is using VFAT or NTFS, you cannot change the permissions. It will *look* like it does (as in your example), but won't actually change anything, and won't give an error message.

If you don't know what format it is, type **mount** in the terminal and it should tell you.

---

### Post by karatekid on 2009-03-25
yes it is vfat.
but this problem arose only recently. I had installed apache some months ago and it was working fine initially but now it doesn't
i am posting the content of fstab.
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
/dev/sda1 /media/windows vfat auto,rw,exec,users,uid=1000,fmask=137,dmask=027 0 0
/dev/sda3 /media/boot vfat auto,rw,exec,users,uid=1000,fmask=137,dmask=027 0 0
/dev/sda5 /media/data vfat auto,rw,exec,users,uid=1000,fmask=137,dmask=027 0 0
/dev/sda6 /media/movies vfat auto,rw,exec,users,uid=1000,fmask=137,dmask=027 0 0
/dev/sda7 /media/vista vfat auto,rw,exec,users,uid=1000,fmask=137,dmask=027 0 0
# Entry for /dev/sda8 :
UUID=0d0b6ff9-7e6f-4069-9e2d-7ab0bb0ca347 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda9 :
UUID=f7d0ee4e-cbda-4285-83de-4762bb48537f none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

```

---

### Post by kanikilu on 2009-03-25
I'm not sure what to tell you...someone correct me if I'm wrong, but my understanding is that vfat does not support unix file permissions.

I haven't tried this myself, but if you want to make it read, write, and execute to all, couldn't you use umask=777 in fstab?

// Edit - or is it umask=000 :confused:

---

### Post by karatekid on 2009-03-25
yes that worked
setting dmask=000 and fmask=003 solved my problem.
Thanx for the quick help.

---

