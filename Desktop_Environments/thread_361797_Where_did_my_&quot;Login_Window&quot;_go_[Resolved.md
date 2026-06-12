---
title: "Where did my &quot;Login Window&quot; go? [Resolved]"
date: 2007-02-14
forum: Desktop Environments
---

### Post by lakelovers on 2007-02-14
When I go to System>Administration>Login Window, it doesn't load. I get the password screen and after that, nothing. How do I recover the "Login Window?" This problem is, apparently, associated with other problems I'm having with GNOME. On the logout screen two options (Log Off & Power Down) are missing. How should I fix this?

---

### Post by haricharan on 2007-02-14
try from terminal and see if you get any error
```
sudo gdmsetup
```

---

### Post by aysiu on 2007-02-14
Or, better yet, the terminal output of this command: ```
gksudo gdmsetup
``` **Always** use *gksudo* or *kdesu* with graphical applications. *sudo* is for terminal-based applications.

More details:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by lakelovers on 2007-02-15
Thanks for your reply. Here's what I get with "gksudo gdmsetup"

```
    X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.   
```

---

### Post by aysiu on 2007-02-15
There seem to be several different approaches to solving that problem:
[Login Window Problem](http://ubuntuforums.org/showthread.php?p=2160315#post2160315)
[GDM fails to start, but can get into Gnome with startx](http://ubuntuforums.org/showthread.php?p=2099962#post2099962)
[Can't launch ``gdmsetup'' [SOLVED]](http://ubuntuforums.org/showthread.php?p=1619354#post1619354)

I'd give each of those a try...

---

### Post by lakelovers on 2007-02-15
I owe you a beer or whatever. I tried the last link, removing "gdm" and "sessreg." Then reinstalled both. Everything seems to be back to normal and I can access the Login Window.

Jerry

---

### Post by aysiu on 2007-02-15
I don't drink beer, but I'm glad it worked out for you.

---

