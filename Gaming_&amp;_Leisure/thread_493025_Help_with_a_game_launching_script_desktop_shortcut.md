---
title: "Help with a game launching script desktop shortcut"
date: 2007-07-05
forum: Gaming &amp; Leisure
---

### Post by cogadh on 2007-07-05
I've been using instructions from a WoW how-to to create small scripts to launch games through Wine and I have them working great when I launch them from a console session. I know I can get them to work from within an existing X session, but I run into a bit of a problem if I try to create a desktop shortcut to launch the script. Here's an example of one of the scripts:
```
#!/bin/sh
#only used if launching from console session
#sudo /etc/init.d/gdm stop

# Launches a new X session on display 3
sudo X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (if necessary)
cd "$HOME/.wine/drive_c/Program Files/LucasArts/SWKotOR/"

# Forces the system to have a break for 2 seconds 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/LucasArts/SWKotOR/launcher.exe"
```
The problem comes when the script hits the "Launch a new X session on display 3" section. Originally, I did not have a "sudo" in the script, but when run from the console, it complains "user not authorized to run the X server, aborting" so I added the sudo and the problem went away. When I create a desktop shortcut for the script (the shortcut runs the command "sh" with the launcher file), I don't get prompted for a password and the script dies silently. I've tried replacing the sudo with gksu and I still don't get a password prompt. I've also tried modifying the shortcut to use gksu and I do get a password prompt, but the script still fails to launch the game. Anyone have any ideas how I can make this shortcut work?

EDIT - Almost forgot, I also replaced the sudo with the line /usr/bin/gksu and that does get me a password prompt, but the script still fails.

---

### Post by hikaricore on 2007-07-05
There's a configuration file somewhere that allows you to change X to allow being started by a normal user.
This would completely solve your problem.

I can't for the life of me remember where it is.  >.<

I saw it mentioned in a guide on the forums once, but can't locate it.

---

### Post by cogadh on 2007-07-05
Yeah, I tried finding something like that too, but no luck. Hopefully someone else will remember how to do it.

---

### Post by cogadh on 2007-07-05
Figured it out, I had to change a line in /etc/X11/Xwrapper.config from "allowed_users=console" to "allowed_users=anybody". Shortcuts work great now! :)

Now I just have to go back to all my launch scripts and remove the sudo...

---

### Post by hikaricore on 2007-07-05
Fantastic.

You know you'd think it would be in some more reasonable place like xorg.conf..

---

