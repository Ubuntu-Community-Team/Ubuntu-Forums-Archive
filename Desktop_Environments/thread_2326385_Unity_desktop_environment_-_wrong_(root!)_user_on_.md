---
title: "Unity desktop environment - wrong (root!) user on elevation prompts"
date: 2016-05-31
forum: Desktop Environments
---

### Post by Nitr0UK on 2016-05-31
I'm using Ubuntu 16.04 desktop, however I'm having issues with the standard elevation prompts that appear when using the Unity desktop environment. Everything appears normal, I am logged in with my standard user account (named dan) and can successfully use this with the sudo command to run elevated commands.

However when asked to elevate when using the unity desktop environment it tells me to authenticate with the root user. I have not modified any settings to do with the root account (re-enabled or otherwise)

It probably goes without saying but as the root user does not have a password I cannot authenticate myself with this account when prompted. I have tried my normal user password and this does not work.

Please see the attached screenshot

Thanks for your time.

---

### Post by mc4man on 2016-05-31
**If** you have gksu (gksudo) installed then run this command & make sure it's set to sudo, not su
```
gksu-properties
```

---

### Post by Nitr0UK on 2016-05-31
Thanks for the quick reply, I've checked gksu-properties and it's set to sudo. On further investigation I believe that Unity is using pkexec instead of gksudo.

If I run a program as gksudo (e.g. gksudo gnome-terminal) this works correctly and asks me to enter my password for my user account and then elevates the process correctly.
If I run a program as pkexec (e.g. pkexec gnome-terminal) it asks me to enter the password for the root user (identical prompt as before) which fails to authenticate when I enter my user password. 

Edit: I have attempted to specify my username using the --user parameter (with the pkexec command), this changes the dialog slightly to "Authentication is needed to run gnome-terminal as user dan" but otherwise continues to prompt for the root user password

Thanks.

---

### Post by grahammechanical on 2016-05-31
When I first noticed that pkexec was being used in Ubuntu I made the mistake of seeing it as a replacement for gksudo. It is not. If I run the command pkexec gnome-terminal I get the same request as you to authenticate as the superuser. And I am not having the problem that you are having.

pkexec works by accessing policy statements in /usr/share/polkit-1/actions. These policy statements decide what level of authentication is required. There is not a policy statement for gnome-terminal. It is my guess that when loading gnome-terminal through pkexec the absence of a policy statement is forcing pkexec to require authentication by the superuser.

Regards.

---

### Post by Nitr0UK on 2016-05-31
Thanks for the replies, I have now fixed this, I added my superuser group (which was previously only defined in sudoers) into the /etc/polkit-1/localauthority.conf.d/51-ubuntu-admin.conf file

---

### Post by mc4man on 2016-05-31
On just a side note  - can't see the reason, purpose or way one would or want to run 'gksudo gnome-terminal' or 'pkexec gnome-terminal'. Doesn't make much sense.
If you already have a terminal open then just switch to root, ie,  sudo su or if from the command prompt (alt+f2)  just go, if gksu is installed  -  
gtk-launch gksu

---

### Post by Nitr0UK on 2016-06-01
I used gnome-terminal as an example only, probably a bad choice of program on my part. Sorry for any confusion

---

