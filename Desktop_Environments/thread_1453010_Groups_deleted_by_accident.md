---
title: "Groups deleted by accident?"
date: 2010-04-12
forum: Desktop Environments
---

### Post by modctek on 2010-04-12
I recently ran into an interesting problem with my Jaunty installation. After popping into System -> Administration -> Users and Groups to change a password on a user account, and checking to see what groups the account belonged to, I saved my changes and continued working.

Unfortunately, something had gone wrong, as all of a sudden, nothing worked. A quick check of the syslog showed that somehow, with my access of the U&G gui app (control panel, in Windows parlance I guess) I managed to delete all my groups! :confused:

Thankfully, the internets pointed me to how to restore the /etc/groups file from my LiveCD (the backup "groups-" was similarly bereft of groups sadly), but obviously, many of the groups created by my installed apps were gone.

I ended up starting afresh with 9.10, but now I'm utterly paranoid of using the U&G gui app. What the heck went wrong?:-k

---

### Post by TitanusEramius on 2010-04-13
It is good to know one should not use the gui for this... Thanks for sharing.

I don't know what went wrong, but I do know that when I am maintaining my servers users & groups I use the terminal to avoid accidents. I did a quick search for a howto I could have posted here but i didn't find any. So unless someone who know what went wrong with your groups, may I suggest reading the man-pages for the terminal-tools to ad/change users & groups:

```
man adduser
``````
man usermod
``````
man groupmod
```And then there is user- & groupdel. The reason I started using the terminal for this kind of system-maintaining is because the file/ftp-server I put up can't run the gui to add & change users on the machine, but once you get the hang of the commands to use, it works (in my opinion, that is :)) far better than the gui.

But let's hope someone who can comment on the gui is willing to share :P

---

