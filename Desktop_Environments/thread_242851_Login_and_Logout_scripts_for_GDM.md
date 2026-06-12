---
title: "Login and Logout scripts for GDM?"
date: 2006-08-24
forum: Desktop Environments
---

### Post by Jabran Asghar on 2006-08-24
Hi,

How we can configure a script to be executed automatically on GDM login, as well as on logout? Actually I want to synchronize two directoris on login and logout using unison ($unison ~/dir1 ~/dir2 -batch). The command works correctly from command line.

I tried adding the command to following files, but no luck:

- .bash_profile: Its not executed when logging in through GDM. 
- .gnomerc: unison says that it could not write to ~/dir2 (is .gnomerc executed as some other user? The ~/dir2 has only user permission "u+rwx", "go=")

- Gnome session startup script option (through GUI) only provides option for login script, so it is not suitable. Also I prefer to use command line for adding the command.


Any ideas?

Jabran

---

