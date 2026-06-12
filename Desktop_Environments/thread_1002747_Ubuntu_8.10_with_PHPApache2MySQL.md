---
title: "Ubuntu 8.10 with PHP/Apache2/MySQL"
date: 2008-12-05
forum: Desktop Environments
---

### Post by r557 on 2008-12-05
I seem to be encountering some odd permissions issues with Ubuntu 8.10 desktop with php, mysql, apache2 loaded on it.

My complete /var/www/ is permissioned as 0777 (it's a development machine on a virtualbox so i'm not overally concerned about Security).

Everytime i attempt to do a file upload through a php script, i'm consistantly being told permission denied.  However, when i view the file directories permissions, they're all 0777.

Any ideas?

**PHP Errors from Wordpress**
[I]Warning: move_uploaded_file(/monn-78746.jpg) [function.move-uploaded-file]: failed to open stream: Permission denied in /var/www/wp-content/plugins/wordtube/admin/functions.php on line 117

Warning: move_uploaded_file() [function.move-uploaded-file]: Unable to move '/tmp/phpo0gOpi' to '/monn-78746.jpg' in /var/www/wp-content/plugins/wordtube/admin/functions.php on line 117[/I]

---

### Post by scragar on 2008-12-05
You're trying to move the file on your root file system?

make sure the path you are moving it to is somewhere in /var/www

---

### Post by r557 on 2008-12-05
> **scragar said:**
> You're trying to move the file on your root file system?

make sure the path you are moving it to is somewhere in /var/www

i knew a second set of eyes would help.

When i look at, Warning: move_uploaded_file() [function.move-uploaded-file]: Unable to move '/tmp/phpo0gOpi' to '/monn-78746.jpg' in /var/www/wp-content/plugins/wordtube/admin/functions.php on line 117

i can now see that wordpress is trying to place the file in the root directory /monn78746.jpg and it's not trying to move it into a folder under /var/www/.

---

### Post by compiledkernel on 2008-12-05
> Unable to move '/tmp/phpo0gOpi' to '/monn-78746.jpg' 

that line puzzles me, your trying to move the file from /tmp to / (root filesystem level)? 

I concur with scragar make sure your path is right.

---

