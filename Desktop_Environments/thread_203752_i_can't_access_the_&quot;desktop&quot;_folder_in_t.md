---
title: "i can't access the &quot;desktop&quot; folder in the terminal..."
date: 2006-06-25
forum: Desktop Environments
---

### Post by cwncool on 2006-06-25
Here's my situation.  I start up the terminal and "su" myself to the root user.  Then I type "dir" to view the folders.  It says "Desktop", which is where my file is located.  I then type "cd /Desktop" and press ENTER.  It tells me there is no such file or directory, even though when I type "dir" it lists it as there.  I need to cd / into my Desktop to get to the folder, but I don't know how.  Is there another way to view my desktop in the terminal? Thanx!

---

### Post by scxtt on 2006-06-25
"cd ~/Desktop" ... which is different from /Desktop (and doesn't exist, in general) ... you're giving an absolute path, based off the / directory, not going from the current directory to Desktop, as "cd Desktop" would do ... and there is a difference b/t "Desktop" for root and a non-root user ... but "cd~/Desktop" will take you to the Desktop of whichever user you are ...

and don't use "dir", use "ls" --- :p

---

### Post by Winblowz on 2006-06-25
First of all, I'd use sudo instead of su. If you want to become super user, just do "sudo -s", or type "sudo" before every command.

Now to your question...The Desktop folder is located at "/home/<username>/Desktop", not "/Desktop." So, if your username is john you would do
```
sudo cd /home/john/Desktop
```

---

### Post by stephen_lau on 2006-06-25
[QUOTE=cwncool] I start up the terminal and "su" myself to the root user.[/QUOTE] 
You don't to go root to view your user's Desktop folder.

> Then I type "dir" to view the folders.
Try using
```
ls
```
Much easier to see folders and files. It's not DOS anymore :P

> I then type "cd /Desktop" and press ENTER.  It tells me there is no such file or directory, even though when I type "dir" it lists it as there.
Your Desktop is stored in /home/[your user name]/Desktop. By typing in ```
cd /Desktop
```, you are trying to access /Desktop, which doesn't exist. Just type ```
cd Desktop
```

---

### Post by aysiu on 2006-06-25
**cd Desktop**: I'm currently in /home/cwncool and I want to be in /home/cwncool/Desktop

**cd /Desktop**: I don't care where I am right now. I want to be in /Desktop (which doesn't exist)

**cd ~/Desktop**: I don't care where I am right now. I want to be in /home/cwncool/Desktop

---

### Post by cwncool on 2006-06-25
thanx guys! this forum's the best!

---

