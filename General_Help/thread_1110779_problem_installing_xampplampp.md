---
title: "problem installing xampp/lampp"
date: 2009-03-30
forum: General Help
---

### Post by dil3ma on 2009-03-30
hey i've been trying to install xampp/lampp but i've had a few problems, once is that when i try to login as the system administrator as root i type in 'su' and it asks for my password but wont let me type it in...
so i tried to write in the terminal what I wanted to do anyway

which was ```
 sudo tar xvfz xampp-linux-1.7.tar.gz -C /opt
```

and i got this:

```

dilema@dilema:~$ sudo tar xvfz xampp-linux-1.7.tar.gz -C /opt
tar: xampp-linux-1.7.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

any help would be appreciated, thank you

---

### Post by kellemes on 2009-03-30
> **dil3ma said:**
> hey i've been trying to install xampp/lampp but i've had a few problems, once is that when i try to login as the system administrator as root i type in 'su' and it asks for my password but wont let me type it in...
so i tried to write in the terminal what I wanted to do anyway

which was ```
 sudo tar xvfz xampp-linux-1.7.tar.gz -C /opt
```

and i got this:

```

dilema@dilema:~$ sudo tar xvfz xampp-linux-1.7.tar.gz -C /opt
tar: xampp-linux-1.7.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

any help would be appreciated, thank you



"su" by default asks for the root-password, there is no root-account setup on a Ubuntu system, and so the password won't work.
And so you use "sudo" (or "gksudo" for graphical apps).
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

I guess the error explains what the problem is, the file is not there..
Are you sure you're in the directory the file is in?
Type "ls" from the prompt to find out.

---

### Post by lovinglinux on 2009-03-30
```
 sudo tar xvfz xampp-linux-1.7.tar.gz -C /opt
``` The command above assumes that the file * xampp-linux-1.7.tar.gz* is in your home directory. The error means that it isn't. To fix this you could use the full path to *xampp-linux-1.7.tar.gz* in the command above. To do this, locate the file on your hard drive, right-click on it and select copy. This will copy the entire path so you can paste it over the command.

The result should be like this:

```
 sudo tar xvfz /home/you/whatever/xampp-linux-1.7.tar.gz -C /opt
```

---

