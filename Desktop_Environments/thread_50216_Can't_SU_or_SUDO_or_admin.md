---
title: "Can't SU or SUDO or admin"
date: 2005-07-19
forum: Desktop Environments
---

### Post by MikeyXX on 2005-07-19
When prompted for my root password in GNOME it works fine. When I'm prompted in KDE it gives me an authentication error. Any suggestions?

michael@linuxlt:~$ su
Password:
su: Authentication failure
Sorry.
michael@linuxlt:~$
 ](*,)

---

### Post by frodon on 2005-07-19
type : ```
sudo su
```

---

### Post by MikeyXX on 2005-07-19
[QUOTE=frodon]type : ```
sudo su
```[/QUOTE]
 Huh? This doesn't make sense. If I use this sudo su and use the password for the user, it works. But if I put the root password in it doesn't. What stops another user from doing this?

---

### Post by frodon on 2005-07-19
Ubuntu doesn't use root account exept if you have created one, all the root tools work with sudo command that why sudo su allow you to become root in a terminal with your user password (by default but you can change the sudo password using "sudo passwd" command). 
If you don't want an user to use sudo command go to System>Administration>User and Group and uncheck sudo permission.

---

### Post by MikeyXX on 2005-07-19
Ahhh, I got it now. So if this works from a prompt, why is it that when it asks for my admin password in the desktop it fails consistantly? Gnome works fine.

---

### Post by frodon on 2005-07-19
[QUOTE=MikeyXX]Ahhh, I got it now. So if this works from a prompt, why is it that when it asks for my admin password in the desktop it fails consistantly? Gnome works fine.[/QUOTE]Strange ... have you changed your admin password before ? Personally I use the user password for both.

---

### Post by FCM on 2005-07-19
I found this helpful

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

Also, when using the command line use: sudo -i

When prompted use your user password and it will put you into root.

Chuck

---

