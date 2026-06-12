---
title: "how to use the shutdown now command in this situation"
date: 2009-05-05
forum: General Help
---

### Post by Kain000 on 2009-05-05
Hey everyone, 

I've been playing with the system monitor applet for gnome and it allows you to set alarms for your system temps in the form of " run this command when temp goes past this level" , ie: shutdown the comp when the processer gets too hot ect.  

my question is what do I need to do to have it run a root command such as shutdown now, without me being at the keyboard to give it the sudo password?

---

### Post by mb_webguy on 2009-05-06
You can edit the sudoers file to allow your user account (and any others you want) to use the shutdown command without using sudo if you want.

Use the command "sudo visudo" to edit the file.  Now look for the line "# User alias specification" and add a list of users as follows:#```
 User alias specification
User_Alias USERS = user1, user2, user3
```Now look for the line "# Cmnd alias specification" and add a command list as follows:```
# Cmnd alias specification
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/reboot, /sbin/halt
```Now look for the line "%admin ALL=(ALL) ALL" and add the command which will let USERS give SHUTDOWN_CMDS without a password```
:%admin ALL=(ALL) ALL
USERS ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS

```
Now those specified users can use the commands "sudo shutdown", "sudo halt", and "sudo reboot" without being asked for your password.

EDIT: By the way, the reason that these commands can't be used by normal users is that Linux was designed as a multi-user system.  You don't want one user shutting down the system while others are using it!

---

### Post by triunenature on 2009-05-06
gksu poweroff

The only issue is, it will request your password before shutting off.

---

### Post by Kain000 on 2009-05-08
> **mb_webguy said:**
> You can edit the sudoers file to allow your user account (and any others you want) to use the shutdown command without using sudo if you want.

Use the command "sudo visudo" to edit the file.  Now look for the line "# User alias specification" and add a list of users as follows:#```
 User alias specification
User_Alias USERS = user1, user2, user3
```Now look for the line "# Cmnd alias specification" and add a command list as follows:```
# Cmnd alias specification
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/reboot, /sbin/halt
```Now look for the line "%admin ALL=(ALL) ALL" and add the command which will let USERS give SHUTDOWN_CMDS without a password```
:%admin ALL=(ALL) ALL
USERS ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS

```
Now those specified users can use the commands "sudo shutdown", "sudo halt", and "sudo reboot" without being asked for your password.

EDIT: By the way, the reason that these commands can't be used by normal users is that Linux was designed as a multi-user system.  You don't want one user shutting down the system while others are using it!


Thanks alot for that, now I dont need to worry about a bum pump frying my system

---

