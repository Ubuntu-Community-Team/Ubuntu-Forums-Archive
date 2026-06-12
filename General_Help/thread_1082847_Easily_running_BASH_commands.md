---
title: "Easily running BASH commands"
date: 2009-02-28
forum: General Help
---

### Post by davideotape on 2009-02-28
I run this code:

```
sudo apt-get autoclean
```

every time I have just installed an update. As I run it so much, I was wondering if there was a way of making a shortcut to the command on my desktop, so whenever I double-click on the shortcut the command runs for me in the terminal.

All help appreciated :D

David

---

### Post by justleen on 2009-02-28
just right click on your desktop, create launcher, and enter the command at the command-field.
Change sudo to gksudo though, so you'll get a password prompt.

---

### Post by insineratehymn on 2009-02-28
There is a few ways to do what you want (isn't there always?)

You can create a bash script containing, easy as opening your favorite text editor, putting that command in it, and saving it as "autoclean.sh".

Make sure you set the permissions to 755 so it can run.

Double click it and it should run away.

Or you can make an [alias]("http://ubuntuforums.org/showthread.php?t=204382") that will run the update, upgrade, and autoclean every time you type something like "update".

---

### Post by lordharsha on 2009-02-28
Right click on the desktop, select "Create Launcher. Choose the Type->Application in Terminal". Give it a name, and type in the command in the Command field.

Since you need sudo privileges, it'll open a terminal, ask you for the password, clean the cache, and close the terminal.

---

### Post by leewebb on 2009-02-28
I think one other option would be to set 

APT:Periodic::AutocleanInterval "1";

 in /etc/apt/apt.conf (where "1" is the number of days between clean ups). 

This means that, unless you are drastically in need of disk space, you can let the system worry about cleaning up every day or so.

(This setting will be read by /etc/cron.daily/apt: see the top of that file for details)

[Note: I haven't tested this, but it seems correct in theory]

---

### Post by lordharsha on 2009-02-28
This could be because I'm using hardy, but that option is in /etc/apt/apt.conf.d/10periodic

---

### Post by davideotape on 2009-03-03
Thanks for all the replys guys, they're all great. I've gone for the launcher option so I can run add it to docky :D

---

