---
title: "Most games not working. Please help!"
date: 2006-06-09
forum: Gaming &amp; Leisure
---

### Post by Sukarn on 2006-06-09
I have a lot of games installed on my system and they were all working a week ago, but now, whenever I try running a game, I get the error "No such file or directory".
For example when I try running Planet Penguin Racer (I have main game package, the data package and extras package), I get the message (Error, to be more specific)```
Could not launch menu item

Details: Failed to execute child process "ppracer" (No such file or directory)
```
The same happens for barrage and a lot of other games. I am still able to play some games like Kbounce.
I have Gnome, KDE, XFCE installed and I'm primarily using Gnome.
I tried **dpkg --purge planetpenguin-racer** and so on for removing the planetpenguin-racer packages (3 in total) and installing them again, but I'm still getting the same error.

Anyone got any idea whats wrong? Is there a way to fix it other than a format and reinstall of the OS?


By the way, the title may be a bit off. I am still able to play return to castle wolfenstein: enemy territory.

---

### Post by charlieg on 2006-06-09
Are you a member of the games group?  Edit /etc/group (sudo gedit /etc/group) and find the line starting 'games' and add your username to the end of it.

---

### Post by Sukarn on 2006-06-10
It turns out that I wasn't a member of the **games** group but I am not and I am still getting the same error.

It looks like this now -

games:x:60:sukarn

Should I attach the whole group file for reference?

---

### Post by Sukarn on 2006-06-10
I just installed XQF and its giving me the same error -
```
Could not launch menu item

Details: Failed to execute child process "xqf" (No such file or directory)
```
I am trying to run all these from the menu as running the command from terminal gives me a command not found error like "bash: xqf: command not found"

---

### Post by charlieg on 2006-06-10
Go to /usr/games/bin and try ./xqf - that should work.  If you are now a member of the games group, you will have needed to restart bash (i.e. open a new terminal) for it to have taken effect.

---

### Post by Sukarn on 2006-06-10
```
sukarn@SUKARN-ASKLAS:~$ cd /usr/games/bin
bash: cd: /usr/games/bin: No such file or directory
```
So I suppose the error was correct in saying "No such file or directory".

There seems to be no directory in /usr/games

EDIT: Thanks, it seems that all of the commands are in /usr/games instead of /usr/games/bin
Now how do I go about fixing that?

---

