---
title: "File permissions help"
date: 2009-06-08
forum: General Help
---

### Post by drummerchrissk on 2009-06-08
I need help with some file permissions stuff.

I'm trying to change some file permissions using
```
chmod go+rwx <name-of-folder>
```

I'm trying to get other users on my system to be able to see and play these files. This works but only for the parent folder I've tried to change. All sub-folders still hold the old permission. I have a lot of files and do not want to go through and individually change each one.

What's an easy fix for this?

---

### Post by synapsys on 2009-06-08
You need an -R switch. You need to tell chmod to recursively change permissions for every file in said folder. 

```
chmod -R go+rwx <name-of-folder>
```

"man" is your friend. To learn more about a particular command like chmod:
```
man chmod
```

---

### Post by Bigtime_Scrub on 2009-06-08
Well I suppose one way to do it would be to run
```
gksu nautilus
```
Enter your password and go into the file system where the files you want are. 

Probably in Filesystem->Home->your_user_name_

and then enclose them all into a big highlighted box. Then right click-> Properties-> Permissions to change them to whatever you want.

---

### Post by drummerchrissk on 2009-06-08
I did a little of both.

I was trying to change music files around. I highlited all and set others permissions to create and delete. This changed all folder permissions but I still could not actually listen to any of the music. Using the -R fixed this.

: D

Thanks to you both!

---

