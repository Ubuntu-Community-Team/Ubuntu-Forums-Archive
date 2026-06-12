---
title: "root login???"
date: 2009-05-13
forum: General Help
---

### Post by jblinuser on 2009-05-13
I am currently taking a scripting class and my prof is using fedora. I am using my ubuntu as a dual boot on my vista laptop. When he tells us to log in he says to log in as root from the login screen. When I try to do this it tells me that administrator login is not allowed. 


Can someone tell me how to fix this? 


My prof tried to figure it out and he was unable to find a file that is called inittab. He said that he would be able to make the changes in that file to allow it but we could not find that file. I dont care how it happens but I really need to be able to log in as root from the login screen. 

Please help.

---

### Post by petrus4 on 2009-05-13
> **jblinuser said:**
> I am currently taking a scripting class and my prof is using fedora. I am using my ubuntu as a dual boot on my vista laptop. When he tells us to log in he says to log in as root from the login screen. When I try to do this it tells me that administrator login is not allowed. 

Ubuntu disallowing root logins is probably actually one of the few things that it actually does right. ;)  From a security point of view, it's a feature, not a bug.

Login normally, and then do either

```

sudo <command>

```

to run individual commands as root, or 

```

sudo su

```

to really login as root.  Root access is not something which should be used indiscriminately, however.

---

### Post by lisati on 2009-05-13
The preferred way of running programs that need "root" access in Ubuntu is with "sudo" - forum policy discourages us from telling people how to enable the "root" account

Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lloyd_b on 2009-05-13
> **jblinuser said:**
> I am currently taking a scripting class and my prof is using fedora. I am using my ubuntu as a dual boot on my vista laptop. When he tells us to log in he says to log in as root from the login screen. When I try to do this it tells me that administrator login is not allowed. 


Can someone tell me how to fix this? 


My prof tried to figure it out and he was unable to find a file that is called inittab. He said that he would be able to make the changes in that file to allow it but we could not find that file. I dont care how it happens but I really need to be able to log in as root from the login screen. 

Please help.

First off, while it is possible to create a root login in Ubuntu, it is prohibited by the forum rules to post a howto on exactly how to do this.

It's also completely unnecessary.  In a terminal window, type "sudo -i", and enter your regular password.  At this point, you have a root shell, which can do everything that you could do with a regular root login.

Lloyd B.

---

### Post by aysiu on 2009-05-13
```
sudo -i
``` will give you a root prompt.

```
gksudo nautilus
``` will give you a root browser.

Any other command can be prefaced with *sudo* to make it run with root privileges.

More details [here](http://ubuntuforums.org/showthread.php?t=716201).

---

