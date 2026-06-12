---
title: "NumBlock always off"
date: 2011-03-15
forum: Desktop Environments
---

### Post by vivamotos on 2011-03-15
Hello, 

I want to know how to disable permanently the numlock event if the user press it don't work.

Do you know how to do it?

---

### Post by vivamotos on 2011-03-16
No answer???? :(

---

### Post by ankspo71 on 2011-03-16
Hi,
I just found this link:
"Enabling Numlock upon login"
[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)
Hope this helps

---

### Post by drs305 on 2011-03-16
Just to confirm - you want to *dis*able the key?...

The Numlock key on my system is 77. You can find it by running "xev" in a terminal and pressing the Numlock key to find the value.

The following command will disable the key:
```
xmodmap -e "keycode **77** = NoSymbol"
```
The command is non-persistent. It has to be run on each login. You can make a script and include it in the Startup list so it runs on each boot for a user or include it in the /etc/ startup folders for universal applicability.

---

### Post by vivamotos on 2011-03-17
Hello,

First of all, It doen't work.

Second, I want to disable permanently the key (num lock)

Third, I explain:

I have the following script to connect to an Unix SO.
#!/bin/bash
numlockx off
xmodmap -e "keycode 77 = NoSymbol" (I've checked keycode 77 with xev)
Xephyr :1 -query <ip> -screen 1024x768x8 -ac -host-cursor -fullscreen

WHEN I CONNECT everything is ok, but in the session if the num lock is lightning (is active) I cant move, resize or close any window. But if it's inactive the num lock everything is ok (and the numeric pad didn't work with num lock active or inactive).

This problem I can fix it with the windows program called WinAxe, this program have the option of: Unlatched NumLock, and if it's active everything is ok, but in linux I don't know how to do it.

Anybody knows?

---

### Post by vivamotos on 2011-03-21
No one knows the problem?

---

