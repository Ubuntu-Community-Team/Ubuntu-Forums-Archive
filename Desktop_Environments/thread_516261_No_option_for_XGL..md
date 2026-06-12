---
title: "No option for XGL."
date: 2007-08-03
forum: Desktop Environments
---

### Post by ATOMICplayer on 2007-08-03
Hello all, this is my very first post. I have been reading through many very informative posts, but now, I must ask a question :)

I used this [link]("http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty") to install XGL on my Ubuntu 7.04 install. When I do a ALT + CTRL + Backspace, unbuntu does not give me an option to change from the defual gnome session to any other type, I only get a space to type my user name and password. Is there something I did wrong, or a key combination I do not know about? Please assist! Thanks in advance. :)

---

### Post by mcduck on 2007-08-03
> **ATOMICplayer said:**
> Hello all, this is my very first post. I have been reading through many very informative posts, but now, I must ask a question :)

I used this [link]("http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty") to install XGL on my Ubuntu 7.04 install. When I do a ALT + CTRL + Backspace, unbuntu does not give me an option to change from the defual gnome session to any other type, I only get a space to type my user name and password. Is there something I did wrong, or a key combination I do not know about? Please assist! Thanks in advance. :)

Did you create the XGL session when you installed it? If not, do it now. Then in the GDM screen (the login window) you need to click on the Sessions or Options button (depends on what GDM theme you use) and under that there's option to select session.

---

### Post by ATOMICplayer on 2007-08-03
I did this:

Now we need to install XGL.

```

sudo apt-get install xserver-xglthe package in the Ubuntu repo works.
```

XGL won't load on its own so we need to write a few scripts to have it start.

```

sudo gedit /usr/local/bin/startxgl.shput this in your startxgl.sh file

```
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-sessionif you experience a bug where you have no restart/shutdown button in the shutdown menu then you need to edit startxgl.sh to this

```
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-sessionnow save and make the script executable
```

```

sudo chmod a+x /usr/local/bin/startxgl.shNow we need to create a way to login and launch that
```

```

sudo gedit /usr/share/xsessions/xgl.desktopput this test into that file
```

```

[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Applicationnow make that script executable

```
```

sudo chmod a+x /usr/share/xsessions/xgl.desktop
```

Does that make XGL available as a selection for a session? I do not get any, as if it is locked to only the standard gnome that came w/ ubuntu.

---

### Post by mcduck on 2007-08-04
Yes, that should work, as long those comments mixed with commands are just errors with forum code-tags and you didn't actually run the commands like you posted them.. ;)

For example you posted this:
```
sudo gedit /usr/local/bin/startxgl.shput this in your startxgl.sh file
```
..and the command to run at this point is this:
```
sudo gedit /usr/local/bin/startxgl.sh
```
..and the rest is just comments..

Anyway, check that the right files are actually there and have correct rights:
```

ls -l /usr/local/bin/startxgl.sh
ls -l /usr/share/xsessions/xgl.desktop
```

edit: By the way, the last step ("sudo chmod a+x /usr/share/xsessions/xgl.desktop") is not needed. The xgl.desktop file doesn't need to be executable.

---

### Post by ATOMICplayer on 2007-08-04
mcduck, I got it working! :)  Thanks very much for your help!! Is there a way I could add compiz and emerald to my startup so I wont have to type it in everytime? Thanks.

---

### Post by mcduck on 2007-08-04
> **ATOMICplayer said:**
> mcduck, I got it working! :)  Thanks very much for your help!! Is there a way I could add compiz and emerald to my startup so I wont have to type it in everytime? Thanks.

Sure, just go to System/Preferences/Sessions and on "Startup Programs"-tab click "New" and add the command you use to launch Compiz (I use "compiz --replace -c emerald").

---

### Post by ATOMICplayer on 2007-08-06
> **mcduck said:**
> Sure, just go to System/Preferences/Sessions and on "Startup Programs"-tab click "New" and add the command you use to launch Compiz (I use "compiz --replace -c emerald").

Your the man! Thanks a million.

---

