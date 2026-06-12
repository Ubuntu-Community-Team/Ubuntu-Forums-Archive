---
title: "Logon Trouble"
date: 2007-06-26
forum: Desktop Environments
---

### Post by butlerapatrick on 2007-06-26
I can not seem to logon to Kubuntu. I get the logon screen. I can type in my password. But when I hit enter the screen goes black and then returns to the logon screen. Please help I do not wish to reinstall.

---

### Post by YoG%*@ on 2007-06-26
hell-o,

can you log in on a terminal? (hit ctrl - alt - f1 to get to a terminal, then try to log in. ctrl - alt - f7 brings you back to the graphical login).

mux

---

### Post by butlerapatrick on 2007-06-26
Yes I can.

---

### Post by YoG%*@ on 2007-06-26
try logging in through the graphical login, then go to the terminal and have a look at 
```

dmesg
tail -f /var/log/messages

```
do they show any error messages?

---

### Post by butlerapatrick on 2007-06-26
dmesg: invalid option --f
Usage: dmesg [-c] [-n level] [-s bufsize]

---

### Post by rillip on 2007-06-26
When this happened to me, it was because there was no disk space free; it could not create the files needed to startx.  From the terminal, try 

```
sudo startx
```

That should give you an error message something like x is already running, if it's not, delete this lock file.  Delete the lock file and try again, when you see x trying to start, it should give you some error output on where the issue is.  If it's the same as mine, you can login with recovery mode, clean up some space, and reboot.

Edit: incidently, I only figured out that the space was full because I was trying to reconfigure x.  So I ran man dpkg (looking for the reconfigure option) and was told it couldn't create the man file, insufficient space.  Talk about full! It's a good thing ext3 reserves space for root by default.

---

### Post by butlerapatrick on 2007-06-26
ok how do I do that?

---

### Post by YoG%*@ on 2007-06-26
> **butlerapatrick said:**
> dmesg: invalid option --f
Usage: dmesg [-c] [-n level] [-s bufsize]

dmesg and tail are two different commands. try using them one after the other. dmesg prints bootup messages, tail shows the last lines of the file you pass to it via the -f option.

---

### Post by butlerapatrick on 2007-06-26
No how do I delete the lock file.

---

### Post by bapoumba on 2007-06-26
At the KDM login screen, hit <CTRL><ALT><F2>, login with your username and password, and run:
```
df -H
```
This will tell you if you are running out of space.
```
sudo aptitude clean
```
(or apt-get) will free some space on your root (/) partition. Look also in your /home if you can free some space.

<CTRL><ALT><F7> to go back to the KDM loggin screen

As an example (/ and /home on separate partitions):
```
~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/hda1              8.3G   3.2G   4.8G  40% /
varrun                 256M   107k   256M   1% /var/run
varlock                256M      0   256M   0% /var/lock
procbususb             256M   107k   256M   1% /proc/bus/usb
udev                   256M   107k   256M   1% /dev
devshm                 256M      0   256M   0% /dev/shm
/dev/hda2               11G   884M   9.1G   9% /home

```

---

### Post by butlerapatrick on 2007-06-26
ok that does not really help I need to get into the computer to remove stuff to logon right.

---

### Post by YoG%*@ on 2007-06-26
> **butlerapatrick said:**
> ok that does not really help I need to get into the computer to remove stuff to logon right.
of course, hit <CTRl><ALT><F2> as bapoumba suggested - this will get you to a terminal, from which you said you can login. then please run the other commands that were suggested and either post the outputs here or tell us, what happened. 

hth

---

### Post by bapoumba on 2007-06-26
> **butlerapatrick said:**
> ok that does not really help I need to get into the computer to remove stuff to logon right.
Do not log in KDM. Log into the terminal session (CTRL-ALT-F2) and run the df. You'll see if you are running out of space. I've pasted mine as an example.
Then run the **sudo aptitude clean**, this will free space, may be enough for you to log back into graphical session.
If not, you'll have to make some more room on your /home.

---

