---
title: "Terminal Password"
date: 2009-05-19
forum: General Help
---

### Post by GCkid7 on 2009-05-19
Can someone tell me if I need special password for terminal and how to create one or is it the same as for logging at start up.
 I'm still begginer with Ubuntu.

---

### Post by Legace on 2009-05-19
> **GCkid7 said:**
> Can someone tell me if I need special password for terminal and how to create one or is it the same as for logging at start up.
 I'm still begginer with Ubuntu.

The password that Terminal will ask is the same as the password you use at stat up.

For example, if you type the following, it will ask for your password. Just enter your password (you won't see anything even if you type something in) and press enter.
```
sudo gedit
```

:)

---

### Post by colau on 2009-05-19
> **GCkid7 said:**
> Can someone tell me if I need special password for terminal and how to create one or is it the same as for logging at start up.
 I'm still begginer with Ubuntu.
If you have an account named "xyz"
```

passwd xyz

```
And if you change the root password
```

passwd root

```

---

### Post by GCkid7 on 2009-05-19
> **Legace said:**
> The password that Terminal will ask is the same as the password you use at stat up.

For example, if you type the following, it will ask for your password. Just enter your password (you won't see anything even if you type something in) and press enter.
```
sudo gedit
```

:)

 Thax Legace for quick replay......

---

### Post by cdenley on 2009-05-19
> **alexandari said:**
> no you can use the same password with which you log in to the system. you might need a root password too. just type ```
sudo passwd
``` into the terminal. you will be asked for your user password,and then it`ll tell you to enter a new unix password. enter the desired password for root and you`r done :)

You DO NOT need to set a root password. In fact, it is strongly suggested that you DO NOT. Posting that command is actually not allowed on this forum for that reason. That post should be ignored.

---

### Post by ActiveFrost on 2009-05-19
> **cdenley said:**
> You DO NOT need to set a root password. In fact, it is strongly suggested that you DO NOT. Posting that command is actually not allowed on this forum for that reason. That post should be ignored.

/Root/ without a password ? Why ? :o

---

### Post by Legace on 2009-05-19
> **cdenley said:**
> You DO NOT need to set a root password. In fact, it is strongly suggested that you DO NOT. Posting that command is actually not allowed on this forum for that reason. That post should be ignored.

Just out of intest, why is it not reccomended to set a root password?

---

### Post by cdenley on 2009-05-19
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by ActiveFrost on 2009-05-19
> **cdenley said:**
> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Excellent piece of information, however, everyone does things in his own way. For me, root user/password is the first thing I do after finishing installation. ~ 1 year of Ubuntu'ing and never saw anything similar to "root permission needed" errors. I guess it's not about to use it or not - more likely it's a discussion about hardware differences and "being lucky" ;)

---

### Post by MartyBuntu on 2009-05-19
> **ActiveFrost said:**
>  ~ 1 year of Ubuntu'ing and never saw anything similar to "root permission needed" **errors**.)
It's not an **error**. It's *solid* advice.

> **ActiveFrost said:**
> I guess it's not about to use it or not - more likely it's a discussion about hardware differences and "being lucky" ;)

"being lucky" is not an option for system critical users running anything more complex than Twitter or Facebook.

---

### Post by ActiveFrost on 2009-05-19
> **MartyBuntu said:**
> It's not an **error**. It's *solid* advice.
If it would be an advice, peoples would not worry about permissions ( which is the main point of not using root password ).

> **MartyBuntu said:**
> "being lucky" is not an option for system critical users running anything more complex than Twitter or Facebook.
Haven't used Twitter and I'm not a member of Facebook, so - as a web developer ( includes web server administration, etc. ), can't see a strong reason of not using su ( root with a password ) command.

---

### Post by Soul-Sing on 2009-05-19
Ubuntu doesn,t come with su, i uses sudo. As simple as can be...:p
use ```
sudo-i
``` as a sort of su

---

### Post by cdenley on 2009-05-19
> **ActiveFrost said:**
> can't see a strong reason of not using su ( root with a password ) command.

It's mostly a bad idea in case the user installs a server which authenticates as local users such as ssh. The server may have an option to disable authentication as root (ssh does, but it's off by default). However, then there is the concern that users may login as root, even through the GUI. This greatly increases your exposure to threats. If someone is trying to guess passwords to gain root access, it helps if they have to know the username of an admin user. An attacker almost always goes for root, and if the root password is disabled, they will never succeed.

If you understand what makes a password strong, use that knowledge when choosing a root password, and know how to disable remote services from authenticating as root, then you're probably fine. However, that doesn't describe all ubuntu users, which is why posting instructions for setting a root password isn't allowed here.

---

### Post by cariboo on 2009-05-19
This thread is getting dangerously close to breaking forum policy as stated [here.]("http://ubuntuforums.org/showthread.php?t=716201"). Just to make it clear:
> Tutorials explaining how to enable the root account for a graphical login or autologin will not be supported on the forums and will be moved to the Jail. Although we believe people should have the freedom to run their computers however they want, we also believe in supporting Ubuntu's security model. You can find or post information elsewhere on the internet regarding graphical Ubuntu root logins; such tutorials do not have to be hosted on the Ubuntu Forums.

I'm going to close this thread.

---

