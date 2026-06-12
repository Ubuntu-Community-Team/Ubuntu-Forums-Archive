---
title: "Help with user login"
date: 2006-09-23
forum: Desktop Environments
---

### Post by Yurij on 2006-09-23
I dont know how but I cant login to Ubuntu.:confused: 
When I get to the loginscreen I enter my uername and
password but then it says wrong username or password :( 
but Im sure its right.

Anyone knows how to fix this?[-o< [-o< [-o< [-o< [-o< [-o< 

I can get into the recovery mode but I have no idea
what to do there.

---

### Post by peabody on 2006-09-23
> **Yurij said:**
> 
I can get into the recovery mode but I have no idea
what to do there.

If you seem to have a working command prompt in recovery mode, type this:

passwd user

It'll then ask you to set a new password.  Type it in (it won't echo to the screen, that's okay) confirm it, then type reboot, hit enter, and see if you can login again.

---

### Post by Yurij on 2006-09-24
When i try that it just say that the username dosent
exists.:( :( 
Isnt it a way to list users and groups?:-k

---

### Post by peabody on 2006-09-26
> **Yurij said:**
> When i try that it just say that the username dosent
exists.:( :( 
Isnt it a way to list users and groups?:-k

That was probably your problem to begin with on the login screen.  You do know that usernames are case-sensitive correct?  At the recovery console type "cat /etc/passwd" and look at the bottom of the output.  The text at the beggining (before the first colon on each line) are the usernames.

---

### Post by unisol on 2006-09-26
reboot in recovery mode that should put you in root, make a backup like this: cp /etc/group /etc/group.old and cp /etc/sudoers etc/sudoers.old, then use nano to edit /etc/group and etc/sudoers  save with ctrl-x, Y to confirm and enter to exit.Or if you dont want to edit you can just type: addgroup username admin

---

### Post by peabody on 2006-09-26
> **unisol said:**
> reboot in recovery mode that should put you in root, make a backup like this: cp /etc/group /etc/group.old and cp **/etc/sudoers** etc/sudoers.old, then use nano to edit /etc/group and **etc/sudoers**  save with ctrl-x, Y to confirm and enter to exit.Or if you dont want to edit you can just type: addgroup username admin

Ack!  Don't tell him to touch sudoers!  If the format of the file isn't correct, or its permissions aren't correct he won't have root access anymore when he boots!  The default sudoers file should grant sudo access to anyone in the admin group.  The user he created during the install *should* be in that group.

---

