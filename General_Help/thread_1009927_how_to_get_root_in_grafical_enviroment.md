---
title: "how to get root in grafical enviroment?"
date: 2008-12-13
forum: General Help
---

### Post by tzg6sa on 2008-12-13
Hi!

A have used Ubuntu for 2 years. Now I had to set up a computer which is used by many users. I thought that I should create a root user to do the administration work (to install and modify things for the other users).
I have done this and I have disabled the use of sudo for the users.
The problem is that now I am not able to log in as root and I can not change to root fully. I can only do it in terminal with the command "su root", but I would prefer the graphical interface (GNOME in my case)...

Was it a bad idea?
How could I log in as root?
If it was a very bad idea, how could I undo these actions and give a sudoer permission for a simple user.
It would be a great if someone could link me a documentation about how should a multiple user system be managed.

Thanks!
Zoli

---

### Post by spiderbatdad on 2008-12-13
The forum rules do not support enabling the root account in Ubuntu. You should lock the password now: ```
sudo usermod --lock root
``` Then to get a root shell for administration ```
sudo -i
```To get a graphical root file browser ```
gksu nautilus  #in ubuntu
or
gksu thunar  #in xubuntu
```

---

### Post by Nepherte on 2008-12-13
Give the user that will be administering the computer sudo privileges, the rest none (or only sudo privileges for specific commands). Enabling root is not by definition a bad idea but Ubuntu uses sudo instead and is therefore not supported on these forums. More information can be found here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tzg6sa on 2008-12-13
Hi!

I don't understand the commands. At first I can not use sudo. I can just switch with "su root" in root mode (what I tried to tell in the first post). And so I can not run the commands which you have written. At second I am afraid even if I do it so I can still not use sudo after it. The sudoers file was too complicated for me and I have no access to the "users and groups" in the menu (maybe it has an another name, I don't use english version of ubuntu)

So please tell me, how could I give the default permissions to the users easily.
Where is a documentation about managing multiple users in Ubuntu?

I know that the forum policy does not allow to tell me how to create a root login, but that's not what I want! It was just a (logical?) idea to manage multiple users who are not familiar with linux yet. (Even if I have written here more than one question they are strongly related to each other and the problem is just only one - so it should not be against the forum policy)

I am not a native english speaker, but i hope, that i have managed to tell my problem exact enough.

Thanks!

---

### Post by tzg6sa on 2008-12-13
reading the "rootsudo"...

---

### Post by tzg6sa on 2008-12-13
I have read the proposed site. Although I still don't know how could I restore the sudoers file in an easy way. The only solution what i have read would be to generate a new user account (with su root) and give them access to sudo. After it I could manage the Users and Groups in the graphical environment.

Do you think it will work?
Is there an easier solution?
Where is a good documentation about managing multiple users?

Thanks!

---

### Post by Titan8990 on 2008-12-13
In a default set up, all users in the admin group have rights to use sudo. Try adding your current user to the admin group:


sudo adduser YOURNAME admin


If you want to use your graphical environment as root, get any distro but Ubuntu.

---

### Post by spiderbatdad on 2008-12-13
your sudoers file should have this line:```
# User privilege specification
root	ALL=(ALL) ALL

```
You may need to boot into recovery mode to edit the file if you cannot presently use 'sudo.'

visudo is the command to edit the file.
if you prefer, an easier editor is nano. so run command (in recovery boot) ```
export EDITOR=nano
nano /etc/sudoers
```ctrl+o to save, enter to confirm, ctrl+x to exit.```
reboot -h now
```

---

### Post by tzg6sa on 2008-12-13
The settings are restored. 
I have chosen the "adduser YOURNAME admin" solution.

---

