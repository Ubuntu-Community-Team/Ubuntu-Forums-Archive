---
title: "XGL for Multipleusers"
date: 2007-04-23
forum: Desktop Environments
---

### Post by hulet on 2007-04-23
Has anyone set up XGL for multiple users using both KDE and Gnome? In this system I setting up for my cousins (ATI X1300 v.c.), if one user was logged in using XGL and then log out, the other user can't log in using an XGL session. I get this error: ```

Fatal Server error:
Could not create server lock file: /tmp/.X1-lock

```

Does anyone know how to solve this? I have tried changing the permission on .X1-lock to make it readable by others, or changing my /usr/local/bin/startxgl.sh files but to no avail.

---

### Post by megalomaniac on 2007-04-30
[FONT=Arial][SIZE=2][COLOR=Black]I had this exact same problem with gnome. I have no idea if there's an actual fix, but I did find this work around...

First you'll need to edit your startxgl.sh:[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]```
sudo gedit /usr/local/bin/startxgl.sh
```[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=Black]Mine looks something like this:[/COLOR][/SIZE][/FONT]```
[FONT=Arial][SIZE=2][COLOR=Black]Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
dbus-launch --exit-with-session gnome-session
rm /tmp/.X1-lock /tmp/.X11-unix/X1[/COLOR][/SIZE][/FONT]
```[FONT=Arial][SIZE=2][COLOR=Black]Which should remove the offenders when you log off, it's the bottom two lines that are important for this.
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]
You'll need to remove them manually the first time though. So log out then hit [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]CTRL+ALT+F1 and login as a user with admin privileges.

Next run:[/COLOR][/SIZE][/FONT]```
[COLOR=Black]sudo rm /tmp/.X1-lock /tmp/.X11-unix/X1[/COLOR]
```[FONT=Arial][SIZE=2][COLOR=Black]Then hit CTRL+ALT+F7 to go back to the login-screen, and bobs your uncle...
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]
[/COLOR][/SIZE][/FONT][COLOR=Black]Couldn't tell you if that works with KDE though.

Hope that helps :)
[/COLOR]

---

### Post by hulet on 2007-04-30
Thanks. That helped a lot. :)
But, sometimes it doesn't though. I don't know why it is acting in this erratic manner.

---

### Post by megalomaniac on 2007-05-01
Odd, works fine for me. Might be worth checking out the XGL section in the Beryl forums, that's where I got a large chunk of the answer from originally.

---

