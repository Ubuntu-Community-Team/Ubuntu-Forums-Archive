---
title: "Ubuntu Logout or Login Script"
date: 2008-07-11
forum: Desktop Environments
---

### Post by Benismyhorse on 2008-07-11
Hi, In my last post I was wanting to make a default desktop, people said Sabayon, I tried but in didn't work but then tried it again and in did, this brings me to my final question (I promise), I want the user's desktop to be reset to the sabayon desktop and after trying I found that if I delete there profile /home/USER then it resets it to the sabayon desktop.
The command I use is rm -r /home/USER, how/where would I put this to get it to run on login and/or logout, but it would be best for logout.:confused:
Please help

Thanks
Shane

---

### Post by edujose on 2008-08-04
You can put the commands you want to run at login in the user's ~/.profile so that they'll run whenever that user logs in. It works even when login through GDM into Gnome.

For logout, the documentation for bash (man bash) says another file gets run, ~/.bash_logout, but I haven't got any success using it (it isn't called when login out of Gnome, nor when shutting down or rebooting) :(.

Anyway, for logout I found [this thread]("http://ubuntuforums.org/showthread.php?t=147007&highlight=.bash_logout&page=2") that says that file /etc/gdm/PostSession/Default allows placing commands inside it to be run when login out of Gnome (that's Gnome-specific, you should find other way if running XFCE or KDE instead of Gnome). I haven' tested it, though.

Another link where this and other login files are explained is [this one]("http://people.uleth.ca/~daniel.odonnell/Blog/lost-in-logout-land-running-scripts-on-login-and-logout-partially-solved-but-interesting-anyway"). It explains /etc/gdm/PostLogin/Default, /etc/gdm/PreSession/Default and /etc/gdm/PostSession/Default.

Aside of this, what do you achieve by running ```
rm -r /home/user
```? :confused: I suppose after that you should put there a replacement directory, like ```
cp -r /home/user_of_reference /home/user
``` or something.

PS: I'm also trying to run a classroom of computers using Ubuntu in september, so these login/logout things are also interesting to mine :).

---

