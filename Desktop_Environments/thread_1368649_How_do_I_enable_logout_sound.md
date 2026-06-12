---
title: "How do I enable logout sound?"
date: 2009-12-30
forum: Desktop Environments
---

### Post by theyain on 2009-12-30
I'm trying to use a script I got from gnome-look to enable the logout sound.  But no matter what I do, it doesn't work.  What am I doing wrong?


```

#!/bin/sh

PATH="/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}
 /usr/bin/canberra-gtk-play --file="/usr/share/sounds/ubuntu/stereo/desktop-logout.ogg"
exit 0

```

And as an added not, I'm using --file= instead of --id= for canberra-gtk-play because I changed the desktop-logout.ogg file to something I want, thus the --id= option doesn't work anymore.

---

### Post by theyain on 2010-01-01
Bump, help please?

---

### Post by jonny163 on 2010-04-28
I'm completely n00b to this but if there is a specified logout noise then surely there is a way to do activate it without having to script anything?

---

### Post by jimmydean886-2 on 2011-06-25
From the code, it looks like it is trying to play the Ubuntu logout sound using an application or command called "canberra-gtk-play". Check synaptic to see if you have it. Also, in the first set of url's, (line 3) the folder they refer to is not always x11r6. If you are using an older system, it may be different. Also: I get a message when I shut down that says that PulseAudio is configured on a per-user basis whenever I startup in safe mode, (getting rid of Plymouth) or shut down on my older machine. This basically means that you can't play anything at that point in time-- the user is already logged out. Maybe someone could find a config file which you could change that? It would probably work if only the logout sound sounded before the session has stopped the Pulse-session.

---

### Post by Arny006 on 2011-11-23
Hi,

go to **System/Settings/Start Programs or Start Applications** and click to start, sorry my system running in German-language!

This application list all auto-start programs! For sure is already a **"GNOME Login Sound"**, if not, click insert and copy/paste following in the respectively fields:

Field: **Name:** GNOME Login Sound

Field: **Command:** /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

Field: **Comment:** Plays a sound whenever you log in

Click Store and you have done!

**For Logout-Sound click again insert and copy/paste following in the respectively fields:**

Field: **Name:** GNOME Logout Sound

Field: **Command:** /usr/bin/canberra-gtk-play --id="desktop-logout" --description="GNOME Logout"

Field: **Comment:** Plays a sound whenever you log out

Click Store and you have done!

Do you wish the same sound for login and logout? Just use the same command at your choice.

Enjoy

---

### Post by jimmydean886-2 on 2011-11-23
I have been looking for a solution for this for some time now, and have found that there already is a logout sound, Pulseaudio just exits too soon.

Try what you can, I've never seen the logout sound idea as a STARTUP application, only shutdown.

---

### Post by jimmydean886-2 on 2011-12-03
I've found it!


BEFORE YOU CONTINUE: This will disable confirmation for log out, but not shut down, where the dialog will appear AFTER the sound is played.

Open up nautilus as root (gksu nautilus) then navigate to /usr/lib/indicator-session

there you will see two items. Rename the one called "gtk-logout-helper" to "gtk-logout-helper-nosound"

Create a blank file called "gtk-logout-helper" to replace the old one and put this text in it.
```
#!/bin/bash
/usr/bin/canberra-gtk-play --id="desktop-logout" --description="GNOME Logout"
echo $1
SHUTDOWN="--shutdown"
LOGOUT="--logout"
RESTART="--restart"
if [ $1 = $SHUTDOWN ]; then
    /usr/lib/indicator-session/gtk-logout-helper-nosound --shutdown
fi
if [ $1 = $LOGOUT ]; then
    gnome-session-quit --no-prompt
fi
if [ $1 = $RESTART ]; then
    /usr/lib/indicator-session/gtk-logout-helper-nosound --restart
fi

```I designed this so that it could be easily changed to meet a changing os's (Ubuntu's) needs.

Enjoy!


PS: **The strategy in the quote below plays the logout sound at login.**
Arny006:
> Hi,

go to **System/Settings/Start Programs or Start Applications** and click to start, sorry my system running in German-language!

This application list all auto-start programs! For sure is already a **"GNOME Login Sound"**, if not, click insert and copy/paste following in the respectively fields:

Field: **Name:** GNOME Login Sound

Field: **Command:** /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

Field: **Comment:** Plays a sound whenever you log in

Click Store and you have done!

**For Logout-Sound click again insert and copy/paste following in the respectively fields:**

Field: **Name:** GNOME Logout Sound

Field: **Command:** /usr/bin/canberra-gtk-play --id="desktop-logout" --description="GNOME Logout"

Field: **Comment:** Plays a sound whenever you log out

Click Store and you have done!

Do you wish the same sound for login and logout? Just use the same command at your choice.

Enjoy

---

