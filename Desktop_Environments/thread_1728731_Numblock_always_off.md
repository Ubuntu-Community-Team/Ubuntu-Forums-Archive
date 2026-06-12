---
title: "Numblock always off"
date: 2011-04-14
forum: Desktop Environments
---

### Post by vivamotos on 2011-04-14
Hello,

First of all, It doen't work.

Second, I want to disable permanently the key (num lock)

Third, I explain:

I have the following script to connect to an Unix SO.
#!/bin/bash
numlockx off
xmodmap -e "keycode 77 = NoSymbol" (I've checked keycode 77 with xev)
Xephyr :1 -query <ip> -screen 1024x768x8 -ac -host-cursor -fullscreen

WHEN I CONNECT everything is ok, but in the session if the num lock is  lightning (is active) I cant move, resize or close any window. But if  it's inactive the num lock everything is ok (and the numeric pad didn't  work with num lock active or inactive).

This problem I can fix it with the windows program called WinAxe, this  program have the option of: Unlatched NumLock, and if it's active  everything is ok, but in linux I don't know how to do it.

Anybody knows?

---

