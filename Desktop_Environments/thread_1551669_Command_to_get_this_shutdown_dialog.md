---
title: "Command to get this shutdown dialog?"
date: 2010-08-12
forum: Desktop Environments
---

### Post by fallenshadow on 2010-08-12
Does anybody know of a command to get this Gnome shutdown dialog?

[IMG]http://i34.tinypic.com/6tmujd.png[/IMG]

---

### Post by fallenshadow on 2010-08-12
Hmm... already I have this partly figured out.

Its called gtk-logout-helper. Now I just need to figure out a command to make it work. :)

---

### Post by kerry_s on 2010-08-12
thats a zenity --question script. i'm guessing something like:

zenity --question --title="Shutdown" --text="are you sure you want to close all programs and shutdown the computer\?" --cancel-label="Cancel" --ok-label="Shutdown"

i use a similar on mine.

```
#!/bin/bash

zenity --question --title="Exit Options" --text="What do you want to do\?" --cancel-label="Shutdown" --ok-label="Log Out"

if [ $? = 0 ]; then
	gnome-session-save --logout-dialog
elif [ $? = 1 ]; then
	gnome-session-save --shutdown-dialog
fi
exit 0

```

---

### Post by fallenshadow on 2010-08-13
Its actually the official shutdown dialog from Gnome session indicator applet.

However I have sorted it now! Thanks for trying to help! :)

---

### Post by sydbat on 2010-08-13
> **fallenshadow said:**
> Its actually the official shutdown dialog from Gnome session indicator applet.

However I have sorted it now! Thanks for trying to help! :)Would you be willing to share?

---

### Post by kerry_s on 2010-08-13
> **sydbat said:**
> Would you be willing to share?

yeap, he's right.

the command:
```
/usr/lib/indicator-session/gtk-logout-helper
```

Application Options:
  -l, --logout             Log out of the current session
  -s, --shutdown           Switch off the entire system
  -r, --restart            Restart the system

---

### Post by fallenshadow on 2010-08-14
Ah you got it Kerry! :)

See once you know what its called a simple file search will find it! 

Then you can check out the file properties to find its location in your filesystem.

I found out the options just by guessing. ( like -l, -r, and -s )They are pretty common sense... s for shutdown etc.

---

### Post by kerry_s on 2010-08-14
> **fallenshadow said:**
> Ah you got it Kerry! :)

See once you know what its called a simple file search will find it! 

Then you can check out the file properties to find its location in your filesystem.

I found out the options just by guessing. ( like -l, -r, and -s )They are pretty common sense... s for shutdown etc.

i just used the "--help" option. i rewrote my zenity script to use it, so i can add it as a single launcher.

```

#!/bin/bash

sel=$(zenity --list --title="Exit Options" --text="Make your selection" --column= "Log Out" "Reboot" "Shutdown")

if [ "$sel" = "Log Out" ]; then
	/usr/lib/indicator-session/gtk-logout-helper -l
elif [ "$sel" = "Reboot" ]; then
	/usr/lib/indicator-session/gtk-logout-helper -r
elif [ "$sel" = "Shutdown" ]; then
	/usr/lib/indicator-session/gtk-logout-helper -s
fi
exit 0


```

---

