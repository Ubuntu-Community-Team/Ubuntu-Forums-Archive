---
title: "User name lost in updating Ubuntu"
date: 2009-04-27
forum: General Help
---

### Post by PauB on 2009-04-27
Hi,

I had 8.10 Ubuntu version. Recently I updated to 9.04.

The 8.10 one was programmed for starting directly without asking me my user name. But now 9.04 version ask me this user name before beginning and I can't start the session. I forgot it!

I remember the password, what I ignore is the user name. Is there a way I could recover it, or should I reinstall Ubuntu again?

Thanks,

---

### Post by change_mode on 2009-04-27
Start with a live CD and look at the /home folder. There should be a folder with your user name in there.

---

### Post by matt the destroyer on 2009-04-27
all user names for the system are stored in /etc/password.

Start the system in recovery mode and select the root console option.  When you have the "#" prompt, type in:

cat /etc/password

To understand the syntax of the file, read this page:
[http://en.kioskea.net/contents/unix/unix-users.php3](http://en.kioskea.net/contents/unix/unix-users.php3)

Also, you can reset the password here if you need to with:
passwd <user_name>

Bonne chance!

---

### Post by PauB on 2009-04-28
Hi. I typed "cat /etc/passwd" and got a large list (larger than the screen) of information, but I don't know how to find this user name among all these lines.

Sorry, if I'm asking something obvious.

---

### Post by Monotoko on 2009-04-28
You dont need to do that, just run the following:

```
cd /home
```
```
ls
```

It will list all the folders in your home partition, which will be the same as your username ;)

---

### Post by nandemonai on 2009-04-28
From recovery mode:

```
ls -l /home/
```

Has to be one of those.

---

### Post by PauB on 2009-04-29
Thanks a lot to all. I could find the user name.

---

