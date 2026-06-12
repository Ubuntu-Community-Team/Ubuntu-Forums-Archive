---
title: "Zenity shutdown script with Consolekit"
date: 2011-08-20
forum: Desktop Environments
---

### Post by crking on 2011-08-20
Somehow we are at the new stage hal deprecated and its  changes is not easy for newbies to follows.  also changing sudoers is a dirty and not safe trick So:
The need for zenity script with these feature:
@ Consolekit
@Logout
@shoutdown
@restart
@suspend 
@my be cancel
is really being felt.
So if someone how is able to change the old zentiy openbox script comes forward and do the job; we are all appreciating.

---

### Post by kerry_s on 2011-08-20
link to "old zentiy openbox script" that your talking about.
i'll have a look, but i'm old & rusty. lucky for you i'm using lubuntu though, so it's openbox.

---

### Post by kerry_s on 2011-08-20
is this the script?
[http://bbs.archbang.org/viewtopic.php?id=279](http://bbs.archbang.org/viewtopic.php?id=279)

---

### Post by kerry_s on 2011-08-20
alright try this 1, i just did it from scratch, so its clean.

```

#!/bin/bash

ask=`zenity --list --title="Logout Options" --text="Your options" --column="0" "Logout" "Suspend" "Reboot" "Shutdown" --hide-header`

if [ "$ask" == "Logout" ]; then
	openbox --exit &
fi

if [ "$ask" == "Suspend" ]; then
	dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend
fi

if [ "$ask" == "Reboot" ]; then
	dbus-send --system --print-reply --dest="org.freedesktop.ConsoleKit" /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart
fi

if [ "$ask" == "Shutdown" ]; then
	dbus-send --system --print-reply --dest="org.freedesktop.ConsoleKit" /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
fi
exit 0

```

looks like this:

---

### Post by crking on 2011-08-20
kerry_s, Thanks you very much mate.

the link to archlinux which you provided is exactly I am talking about. 

That was great and also clean. very much thank you.

```
AND NOW WE HAVE NEW ZENITY OPENBOX SCRIPT.

```
> [SIZE="2"]and if it is not two much to ask, how could we add bullet buttons. [/SIZE]    ;D

again you rock.

---

### Post by kerry_s on 2011-08-20
bullet buttons? got a pic?

zenity is a bit limited.

---

### Post by crking on 2011-08-20
what about this:

[IMG]http://static.inky.ws/image/605/image.jpg[/IMG]

---

### Post by kerry_s on 2011-08-20
> **crking said:**
> what about this:

[IMG]http://static.inky.ws/image/605/image.jpg[/IMG]

what about it? do you mean you want the useless circles on the front? :D

change the zenity line to this:
```

zenity --list --title="Logout Options" --text="Your options" --radiolist --column="Select" --column="Type" false "Logout" false "Suspend" false "Reboot" false "Shutdown" --height="220"

```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=200431&stc=1&d=1313839722[/IMG]

---

### Post by crking on 2011-08-20
No not at all as i said before your script is absolutely clean.
and if the change you said after change the totally of that we don't want anything more
thanks.

---

### Post by crking on 2011-08-20
How about hibernate. what should we use ???

```
Does change user fit in this area?
```

---

### Post by kerry_s on 2011-08-20
> **crking said:**
> How about hibernate. what should we use ???

```
Does change user fit in this area?
```

```

if [ "$ask" == "Hibernate" ]; then
	dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Hibernate
fi

```

> Does change user fit in this area?


i don't think there is a switch user installed on any base linux.
i'm sure we could include whatever program you choose to do that.

---

