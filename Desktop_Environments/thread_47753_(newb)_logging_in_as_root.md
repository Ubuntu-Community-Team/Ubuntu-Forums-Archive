---
title: "(newb) logging in as root"
date: 2005-07-09
forum: Desktop Environments
---

### Post by Flakes on 2005-07-09
it says i have to log in as root from the console so i ctrl alt esc and log in that way, whats the command to run gnome?

---

### Post by javiadip on 2005-07-09
startx will start gnome

btw, root account is disabled in ubuntu, If it asks you for your root password, its the same password u use for your user account. In terminal use sudo -s instead of su. To execute any command, 'sudo <commands>

For more information on using sudo visit  [https://wiki.ubuntu.com/NewUbuntuUsers](https://wiki.ubuntu.com/NewUbuntuUsers)

---

### Post by Flakes on 2005-07-09
well, what i'm trying to accomplish is to get gnomad2 running as root, is there an alternate way to do that?

---

### Post by javiadip on 2005-07-09
[QUOTE=Flakes]well, what i'm trying to accomplish is to get gnomad2 running as root, is there an alternate way to do that?[/QUOTE]

Ive never used that package before, but you can try typing sudo gnomad2 in terminal window, and type in your user password,

---

### Post by Flakes on 2005-07-09
[QUOTE=javiadip]Ive never used that package before, but you can try typing sudo gnomad2 in terminal window, and type in your user password,[/QUOTE]
 finally it works! thanks :)

---

