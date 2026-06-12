---
title: "I want an icon on my desktop to always run as root..."
date: 2005-05-06
forum: Desktop Environments
---

### Post by fizgig on 2005-05-06
I have a script on my desktop that mounts a remote samba share to my computer.  I'd like to just double-click on the script and have it run but it needs to be run as root since it uses the mount command.  

I'd just like to have the program run as root when I double-click it - ideally without having to enter the root password.  Is this possible?

---

### Post by bored2k on 2005-05-06
The launcher should be something like
gksu "command.sh" [this will ask for ROOT password] or
gksudo "command.py" [user password]

You could edit your visudo file so the commands you run dont require any passwords at all, but you probably dont want this.

---

### Post by fizgig on 2005-05-06
[QUOTE=bored2k]The launcher should be something like
gksu "command.sh" [this will ask for ROOT password] or
gksudo "command.py" [user password]

You could edit your visudo file so the commands you run dont require any passwords at all, but you probably dont want this.[/QUOTE]

Thanks for the help.  It works but it asks for my password.  Half of the way there.

---

### Post by bored2k on 2005-05-06
[QUOTE=fizgig]Thanks for the help.  It works but it asks for my password.  Half of the way there.[/QUOTE]
 If you edit your visudo correctly, it wont.
```
export EDITOR=gedit && sudo visudo
``` 

Read the manual first..

---

### Post by rwabel on 2005-05-06
I was trying to do something simliar. I put that line in my sudoers

myusername   hostname = NOPASSWD:    /usr/bin/apt-get

but I still get asked for the password. What am I missing? Do I've to restart sudoers or sth like that to accept the changes?

---

### Post by Takis on 2005-05-06
Can't you set the mount option so that any user can mount it? That way you wouldn't need a password.

---

