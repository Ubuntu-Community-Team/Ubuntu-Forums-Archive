---
title: "Attempting to change window manager to i3 prevents me from logging in"
date: 2024-07-24
forum: Desktop Environments
---

### Post by zedzee on 2024-07-24
After installing i3 (with sudo apt install i3), I went to the login screen to select i3 as the window manager. After selecting i3, I tried to log into my account, but it just kicked me back to the user select screen.

How could I fix this? I would really like to be able to use i3.

Version: Ubuntu 24.04

---

### Post by currentshaft on 2024-07-24
Try pressing Control-Alt-F4 to get a non-graphical login console, log in with your username and password, run "sudo dmesg" to check for errors, if there aren't any, then "ls -ltr /var/log | tail" to see the most recent logs and check them.

---

