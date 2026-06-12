---
title: "adding nice command to wow launcher"
date: 2007-09-03
forum: Gaming &amp; Leisure
---

### Post by ministoat on 2007-09-03
is it possible to add a nice command to my desktops WoW launcher? it'd be nice to not have to atl-tab to terminal and renice :)

---

### Post by cogadh on 2007-09-03
Since raising a running processes scheduling with nice or renice requires sudo or root, and running a Wine app with sudo or as root is really bad thing to do, I'm not sure you could do it effectively. The problem is, the Wine app would have to be launched and then after it is running, you would have to somehow enter your password to use sudo without ALT-TABbing back to the terminal. You wouldn't be able to run the launch script with sudo, since that would run Wine with sudo permissions and adding sudo to the renice line in the script wouldn't work since you are still stuck having to ALT-TAB to get back to the terminal and enter the password. I think the script would have to be done something like this, but I can't think of any way that it could work:
```
#!/bin/sh
# Goto game dir 
cd "$HOME/.wine/drive_c/Program Files/Game/Directory/"

# Launches game
WINEDEBUG=-all wine "C:/Program Files/Game/Directory/game.exe"

# Renice the app
sudo renice -n -10 game.exe
```

---

### Post by ministoat on 2007-09-03
hmm thanks for trying but i've read before (maybe a post of yours) that wine shouldn't be run with sudo..i guess i can renice from the terminal ;)

---

### Post by arsenic23 on 2007-09-03
Ok, since the default sudo lets you use it a set amount of time after you input the password, couldn't you do something pointless with sudo as the first command in your script?

Like [COLOR="DarkRed"]*sudo ls*[/COLOR] or something ?  Then a few seconds later when the other sudo command is run it wouldn't need the password.

maybe?

---

### Post by DoktorSeven on 2007-09-03
Add renice as a NOPASSWD to your sudoers.

**EDITOR=gedit gksudo visudo**
(for kubuntu: **EDITOR=kedit kdesu visudo** )

Add this as the last line:
**%admin ALL=NOPASSWD: /usr/bin/renice**

It will no longer ask for password.  (Note: DO NOT just change it to let everything be executable without a password, this is a bad, bad thing.)

---

### Post by cogadh on 2007-09-03
If you do that, then the script would just need a pause added between the game launch and the renice command and it should work perfectly.

EDIT - I wonder, could there be any significant security risk involved in opening up renice to all users?

---

### Post by DoktorSeven on 2007-09-04
I'm sure it could potentially cause some sort of issue, but generally it's not as dangerous as opening some other commands to be ran as root passwordless.

As always, you just have to realize the risks in letting any command run as root without any security measures in place and decide whether the risk is worth it.

---

### Post by deadlydeathcone on 2007-09-04
> **arsenic23 said:**
> Ok, since the default sudo lets you use it a set amount of time after you input the password, couldn't you do something pointless with sudo as the first command in your script?

That seems about right.. "sudo -v" merely extends the sudo timeout without having to run anything, making it perfect.

edit:

Here's a working version:

```
#!/bin/sh
RENICE()
{
        sleep 3s;
	for a in `pgrep $1`; do `sudo renice -10 -p $a > /dev/null`; done
}

sudo -v
wait

# Go to game dir 
cd "$HOME/.wine/drive_c/Program Files/"

# Renice the app
RENICE app.exe &

# Launches game
WINEDEBUG=-all wine app.exe
```

---

### Post by ministoat on 2007-09-04
sounds good - how exactly do i add it to my launcher? :)

---

### Post by deadlydeathcone on 2007-09-12
Create a text file, and copy the stuff I posted above into it. Right click on the file, choose "Prooperties", go to the Permissions tab and check the box that let's it be run as a program. Then, run it via terminal.

You might also check out the script in my signature - it does the same thing, and might be easier.

---

