---
title: "Normal home directory permissions?"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Fraoch on 2006-08-28
I set up samba and in my Windows way of thinking I wanted my samba share to be my home/<normaluser> directory.  Kinda like My Documents right?  Guess not.

So following the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=202605") I changed permissions of /home/mark to 777.

Now when I log in I get an error message:

> User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by the user and not writeable by other users.

It does let me in after that, but I notice I've made some changes that aren't being saved.

I tried to change /home/mark to 644 and wow, that doesn't work.:o   

> Your session lasted less than 10 seconds.  Reboot using failsafe mode.

I did, changed /home/mark to 777 and got back in again with the error message.

I should change /home/.dmrc to 644 I guess, but what about the rest of the directory?  I can't change it to 644 as I can't log in after that.

What's the normal permission level of the home/<normaluser> directory?  Thanks!

P.S.  I now have a /home/samba directory with 777 permissions that seems to work fine for samba.

---

### Post by louis_nichols on 2006-08-28
Permissions for the home folder are best set to 700. the file .dmrc though might have special needs. It's safe to delete it, though, and it will be re-created as needed at next login.

---

### Post by Fraoch on 2006-08-28
Awesome, I'll try it in a bit.  Thanks.

---

### Post by Fraoch on 2006-08-28
Cleared it right up, thanks.

I set .dmrc to 750 as in this thread: [http://ubuntuforums.org/showthread.php?t=233110](http://ubuntuforums.org/showthread.php?t=233110)

---

