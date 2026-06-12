---
title: "How do I log out users?"
date: 2006-07-24
forum: Desktop Environments
---

### Post by ardchoille on 2006-07-24
I have 6 users on this computer (Ubuntu 6.06) and they follow a computer use schedule (ex: user 1 from 2pm to 3pm, user 2 from 4pm to 5pm,etc.). I use cron to unlock/lock the accounts so none of the users "run over" into another users' time. What I want to be able to do is use a cronjob to log out the users when their session are over. How would I do that?

I thought of using Zenity for a nice gui message box with the following command so the users can log themselves out, but they don't remember to log out:

```

zenity --info --title=Reminder --window-icon=/usr/share/icons/Bluecurve/32x32/actions/history.png --text="Your computer session will expire in 10 minutes. Please save all work and remember to log out in 10 minutes."

```

The above command opens a messagebox as shown in the image attachment.

The problem is that when run from cron, cron doesn't specify a DISPLAY, so the message box nevers pops up. Is there a way to tell cron to use DISPLAY=:0.0 or is there a way to pop up this message via another command/app at a specified time? Or, better yet, is there a way to log the users out at a certain time using cron or another app?

---

### Post by gborzi on 2006-07-24
From the output of *zenity --help-gtk*:> ...
--display=DISPLAY           X display to use
...

---

### Post by ardchoille on 2006-07-24
> **gborzi said:**
> From the output of *zenity --help-gtk*:

I also just found another way to do it:

```

env DISPLAY=:0 zenity --info --title=Reminder --window-icon=/usr/share/icons/Bluecurve/32x32/actions/history.png --text="Your computer session will expire in 10 minutes. Please save all work and remember to log out in 10 minutes."

```
That tells cron to use the correct DISPLAY for that command.

Thank you for your reply, I'll use your way, since it integrates better with zenity :)

---

### Post by ardchoille on 2006-07-24
Now that the reminder is taken care of, anyone know how to log a user out at a specified time?

---

### Post by JoWilly on 2006-07-24
I don't know if there is anyway to do this properly in gnome/gdm.

But what you can do is force a logout by killing the user's processes (you should display a warning with zenity so the user knows that his work will not be saved !): setup cron to kill all user processes at a specific time with "pkill -u <USER_NAME>".

You can also use this script (local and vnc users will be logged off):

------------------------------------------------

#!/bin/sh
#
# Author: Tim Van Wassenhove
# Update: 12-12-2003 13:15
#
# This script kills all processes that are owned by a given user.
#

if [ -n "1" ]
then
ps -ef | grep $1 | grep -v grep | awk ‘{ print }’ | xargs kill -9
else
echo "Usage: killuser.sh username"
fi

-------------------------------------------------

---

### Post by ardchoille on 2006-07-24
> **JoWilly said:**
> I don't know if there is anyway to do this properly in gnome/gdm.

But what you can do is force a logout by killing the user's processes (you should display a warning with zenity so the user knows that his work will not be saved !): setup cron to kill all user processes at a specific time with "pkill -u <USER_NAME>".

You can also use this script (local and vnc users will be logged off):

------------------------------------------------

#!/bin/sh
#
# Author: Tim Van Wassenhove
# Update: 12-12-2003 13:15
#
# This script kills all processes that are owned by a given user.
#

if [ -n "1" ]
then
ps -ef | grep $1 | grep -v grep | awk ‘{ print }’ | xargs kill -9
else
echo "Usage: killuser.sh username"
fi

-------------------------------------------------


Thank you very much! This is awesome.. I'll use this method :)

---

### Post by metalheart on 2006-07-24
The Gnome logout command is
```
/usr/bin/gnome-session-save --kill --silent
```

---

### Post by JoWilly on 2006-07-24
> **metalheart said:**
> The Gnome logout command is
```
/usr/bin/gnome-session-save --kill --silent
```

So here we go ! Nice, thanks for the info.

This is probably the better way as it "should" (?) take care of saving the gnome settings properly. You can then follow this with killing the remaining user processes to make sure everything is cleaned out.

---

### Post by ardchoille on 2006-07-24
> **metalheart said:**
> The Gnome logout command is
```
/usr/bin/gnome-session-save --kill --silent
```

AWESOME!!! This is what I have been looking for. Thank you very much! :-D

Give that man a cigar :)

---

### Post by Stevko on 2006-08-29
I have similar problem - logging users out. I have more users and sometimes they let omputer running locked. I can of course log in. Howver is there a way to log them out. When I do "sudo su <username>" and run "gnome-session-save --kill --silent" I just get error message ```
Xlib: connection to ":20.0" refused by server
Xlib: No protocol specified
(gnome-session-save:19407): Gtk-WARNING **: cannot open display:

```
Can I log them out somehow?

---

