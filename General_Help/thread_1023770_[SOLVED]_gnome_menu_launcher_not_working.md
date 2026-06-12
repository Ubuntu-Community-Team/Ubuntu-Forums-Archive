---
title: "[SOLVED] gnome menu launcher not working"
date: 2008-12-28
forum: General Help
---

### Post by Naegling23 on 2008-12-28
So, I am trying to add a launcher to the gnome menu, but it refuses to launch the application.  If I browse directly to the file, and click on it, it runs, but once I create a menu item, nothing.  I have full permissions on it, I just cant figure out whats going on...is there any ideas of what I could be doing wrong here?

---

### Post by taurus on 2008-12-28
Is that file on your path?

When you created a launcher for it, did you include the whole path to that file or just only the name, the executable file?

---

### Post by Naegling23 on 2008-12-28
ok, so an update.  I can create other launchers, just not for the app im trying to link to.  If I create a link in the folder it works, but if I drag it to the desktop, it no longer functions....its odd, but it must be some sort of permissions issue...any help or suggestions?

---

### Post by drs305 on 2008-12-28
To get the proper run path, enter this in terminal:
```

which <appname>

```
Example:  *which gimp*
*/usr/bin/gimp*

When you make the launcher, use whatever the result is above as the run command.

If it still doesn't work, please tell us the app you are trying to run. If it does work, please mark the thread 'Solved'.

---

### Post by Naegling23 on 2008-12-28
so, if I make the file executable, it doesnt launch.  If I make it not, then I get the following error:

Failed to execute child process "/home/pangolin/nwn/nwn" (Permission denied)

this is such a simple task, its driving me crazy that I cant figure it out.

---

### Post by Naegling23 on 2008-12-28
ok, didnt realize anyone had replied, so ill fill in more details

Im trying to launch the file nwn 

its located in /home/pangolin/nwn

I have given the folder nwn full permissions (sudo chmod -R 777)

I have made the nwn file executable.

If I browse to the folder and click on nwn, the game launches.

If I create a link and click on it, the game launches.

If I drag the link to my desktop and click on it, nothing happens.

---

### Post by taurus on 2008-12-28
What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

---

### Post by Naegling23 on 2008-12-28
alright, thanks for the help, I finally figured it out

the file nwn contains additional commands to launch the game.

I added 

cd /home/pangolin/nwn 

to the start of the nwn script.  Now everything is working.

I had tried it before without success, I must have mistyped something though.  grrr...dont know why this was so hard, ive done it hundreds of times before...thanks for all the input, it helped me narrow it down.

---

