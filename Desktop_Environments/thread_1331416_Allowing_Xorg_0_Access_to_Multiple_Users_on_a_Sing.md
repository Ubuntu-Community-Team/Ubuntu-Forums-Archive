---
title: "Allowing Xorg :0 Access to Multiple Users on a Single Host?"
date: 2009-11-19
forum: Desktop Environments
---

### Post by georgelenzer on 2009-11-19
Since 'xhost' is not recommended for use (and doesn't appear to work per user locally) in providing access to an Xorg server instance how does one go about allowing multiple users on a single system to use the :0 screen?

My need (not a rare one by any stretch of the imagination):

1. I am logged in as user1 and have my apps running on my desktop.
2. I need to run other apps as other users on the system.  In this particular instance I need Firefox 2.0 and I don't want it messing with user1, so I run it as user2.

What happens right now:

```
user1@0000s035:~$ su - user2
Password: 
user2@0000s035:~$ cd 
user2@0000s035:~$ cd .approot/bin/
user2@0000s035:~/.approot/bin$ ./ff2launch 
No protocol specified

(firefox-bin:27471): Gtk-WARNING **: cannot open display: :0.0
```Or:

```
user1@0000s035:~$ sudo -u user2 /home/user2/.approot/bin/ff2launch
[sudo] password for user1: 
No protocol specified

(firefox-bin:2000): Gtk-WARNING **: cannot open display: :0.0
```I know that I could run 'xhost +' to allow any user or host to connect, but that's not what I want to do.  If I try adding 'user2' with xhost using either form of options, this is what I get:

```
user1@0000s035:~$ xhost + user2
xhost:  bad hostname "user2"

user1@0000s035:~$ xhost user2
xhost:  bad hostname "user2"

```So how does one run X applications as different users on the same machine?

---

### Post by Michael Matthews on 2009-11-19
Try xhost localhost. See if that works. Of course xhost + should work but that means anyone anywhere can write to your display.

---

### Post by georgelenzer on 2009-11-20
Great idea, unfortunately it didn't work only 'xhost +' works which is very bad...:

```
user1@0000s035:~$ xhost + localhost
localhost being added to access control list
user1@0000s035:~$ su - user2
Password: 
user2@0000s035:~# xeyes
Error: Can't open display: 
user2@0000s035:~# export DISPLAY=localhost:0
user2@0000s035:~# xeyes
Error: Can't open display: localhost:0

```

> **Michael Matthews said:**
> Try xhost localhost. See if that works. Of course xhost + should work but that means anyone anywhere can write to your display.

---

