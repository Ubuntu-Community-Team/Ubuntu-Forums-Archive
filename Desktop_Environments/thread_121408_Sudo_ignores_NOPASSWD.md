---
title: "Sudo ignores NOPASSWD"
date: 2006-01-25
forum: Desktop Environments
---

### Post by ubuntuuser on 2006-01-25
Hi all. I wrote two small scripts that (de-)activate my ethernet adapter. I didn't want to enter any password, so I started visudo and added the following line to the sudoers file:```
username   ALL = NOPASSWD: /sbin/ifconfig, /sbin/dhclient

```
The startup script does ```
sudo ifconfig eth1 up
sudo dhclient eth1
``` and the stop script simply is ```
sudo ifconfig eth1 down
```.
Those scripts do what I want, but I am still asked for a password. What am I doing wrong?

---

### Post by ubuntuuser on 2006-01-28
Anyone?

---

### Post by chris_andrew on 2006-01-28
May I suggest you post your question, here:

[http://www.debianhelp.org/module-pnForum-viewforum-forum-21.html](http://www.debianhelp.org/module-pnForum-viewforum-forum-21.html)

Thanks,

Chris.

---

### Post by earobinson on 2006-01-28
or [http://www.ubuntuforums.org/forumdisplay.php?f=39](http://www.ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by olddog55 on 2006-01-28
Is the new line above or below your 'normal' sudoers line? [  I'm assuming you use sudo in password mode.]

I believe sudo reads top down.  And if your more generic 'require password' permissions line is above, that's what will be acted on.

Move your ifconfig permission line to a position just above it.

/d

---

### Post by ubuntuuser on 2006-01-29
[QUOTE=olddog55]Is the new line above or below your 'normal' sudoers line? [  I'm assuming you use sudo in password mode.]

I believe sudo reads top down.  And if your more generic 'require password' permissions line is above, that's what will be acted on.

Move your ifconfig permission line to a position just above it.

/d[/QUOTE]
That's a good idea, but my /etc/sudoers contains only one line with my username. But I have another idea: When I create a new user using the built-in GNOME dialog, I have the option to let that user run administrative programs (it's a checkbox on the last tab, I don't know the exact English translation). Could that option somehow interfere with the content of /etc/sudoers? Where is that setting saved? It's not saved in the sudoers-file, because there is only the line I added manually.

---

### Post by olddog55 on 2006-01-30
Hmmm.  After playing around a little bit, it would seem that a.) my previous comment was wrong, and b.) the documentation is slightly incorrect. (call it a bug or is it only on my system?)  There seem to be two options:

Option 1 - If you want to enter a sudo password for all commands except your desired ones:

Counter to what is expected, the order is PASSWD:, NOPASSWD:.  Here is my sudoers line:

  username     ALL = PASSWD: ALL, NOPASSWD: /sbin/ifconfig, /bin/cat, /bin/more

Option2: - You want to block all commands except the specified ones: [Note the '(ALL)']

  username     ALL = (ALL) NOPASSWD: /sbin/ifconfig, /bin/cat, /bin/more  

RTFM doesn't always help.  Hacking is fun.  And as always, YMMV, but both these worked for me.

/d

---

