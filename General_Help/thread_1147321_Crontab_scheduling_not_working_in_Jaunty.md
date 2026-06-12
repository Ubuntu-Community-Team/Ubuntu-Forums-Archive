---
title: "Crontab scheduling not working in Jaunty"
date: 2009-05-03
forum: General Help
---

### Post by legatek on 2009-05-03
Hello, I am trying to run a script, changewallpaper.sh, using crontab. The script works fine from the command line, but won't run at the specified time from cron. Here's the output of crontab -l:

```
# m h  dom mon dow   command
*/5 * * * * /bin/changewallpaper.sh
*/2 * * * * /bin/touch /home/monkey/Desktop/test
@reboot	/bin/changewallpaper.sh
```

The times are absurdly short so I don't have to wait long to see if any changes work. I threw in a piece of junk to create an empty file on my desktop, and that works. The @reboot command also works; I get a new desktop each time I reboot, but it won't execute the script based on time. Any idea what's going wrong?

---

### Post by geirha on 2009-05-03
Change the line to ```
*/5 * * * * /bin/changewallpaper.sh &>/tmp/command-output.txt
```

Then wait for the command to run, and see what it output in /tmp/command-output.txt.

If you install the [bsd-mailx](apt:bsd-mailx) package (just mailx in older Ubuntu releases), cron will send you a mail with the output of a command if it produces any output. You read such mails by running ```
mail
``` in a terminal.

---

### Post by legatek on 2009-05-03
I made the change and cron creates the file, but there's no output. I notice that my script uses gconftool-2, which others are having a problem with also.

---

### Post by geirha on 2009-05-03
I think in newer Ubuntu releases, gconftool-2 needs to know the display to alter configuration for. To test if that is the case, you can try setting the DISPLAY variable for that command in the script.

```
DISPLAY=:0.0 gconftool-2 ...
```

The display isn't necessarily :0.0, but if you are the only user logged in, you'll generally have DISPLAY=:0.0

---

### Post by legatek on 2009-05-03
Adding the DISPLAY option doesn't seem to be working either. After a little digging I came across this web page:

[http://sriunplugged.blogspot.com/2008/11/automatic-desktop-wallpaper-changer.html](http://sriunplugged.blogspot.com/2008/11/automatic-desktop-wallpaper-changer.html)

which says that the DBUS_SESSION variable has to be set to use gconftool-2 in cron. I changed my script to be consistent with this suggestion:

```
# Get dbus session for gconftool-2
ON_USER=$(cat /etc/passwd | grep :1000: | cut -d ':' -f 1)
export DBUS_SESSION=$(grep -v "^#" /home/$ON_USER/.dbus/session-bus/`cat /var/lib/dbus/machine-id`-0)

# start of gconftool command and set the desktop

sudo -u $ON_USER $DBUS_SESSION /usr/bin/gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$picsfolder$randomfile"
```

But the script won't work at all. Here is the output from running it in the terminal with and without sudo:

```
monkey@monkey-laptop:/bin$ changewallpaper_dbus.sh 
grep: /home/monkey/.dbus/session-bus/23f5d97cc113405423ce8d6749f22062-0: Permission denied
monkey@monkey-laptop:/bin$ sudo changewallpaper_dbus.sh 
Error setting value: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

```

---

### Post by lovinglinux on 2009-05-03
Try adding this to the cron:

```
USER=[color=#FF0000]monkey[/color]
HOME=/home/[color=#FF0000]monkey[/color]
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/[color=#FF0000]monkey[/color]/bin
DISPLAY=:0.0
MAILTO=[color=#FF0000]monkey[/color]

*/5 * * * * /bin/changewallpaper.sh [color=#33CC00]>/dev/null 2>&1[/color]
*/2 * * * * /bin/touch /home/monkey/Desktop/test
@reboot	/bin/changewallpaper.sh 
```

Change the user in red accordingly.

This worked for me on a similar situation, where the script runs fine in the command line, but not from cron. Declaring the display and using [color=#33CC00]>/dev/null 2>&1[/color] after the problematic script should fix it.

---

### Post by legatek on 2009-05-04
Thanks for the suggestion, but that didn't work either. I guess I'm going to have to wait for a fix from an update, or figure out how to get the changes made in post 5 to stop erroring at me in the console before adding it to cron.

---

### Post by geirha on 2009-05-04
I don't know enough about dbus to know the proper way to get the dbus session address, but you could grab it from nautilus' environment. If nautilus isn't running, there's no point in changing the wallpaper, since nautilus is the program that draws the wallpaper.

Haven't had a chance to test this myself yet, since I'm currently running Hardy and don't have the same problem.
```

# Get the pid of nautilus
nautilus_pid=$(pgrep -u $LOGNAME -n nautilus)

# If nautilus isn't running, just exit silently
if [ -z "$nautilus_pid" ]; then
  exit 0
fi

# Grab the DBUS_SESSION_BUS_ADDRESS variable from nautilus's environment
eval $(tr '\0' '\n' < /proc/$nautilus_pid/environ | grep '^DBUS_SESSION_BUS_ADDRESS=')

# Check that we actually found it
if [ -z "$DBUS_SESSION_BUS_ADDRESS" ]; then
  echo "Failed to find bus address" >&2
  exit 1
fi

# export it so that child processes will inherit it
export DBUS_SESSION_BUS_ADDRESS

# Change the wallpaper
gconftool-2 ...

```

---

### Post by legatek on 2009-05-04
Bravo! That finally works! Thanks a lot. Marking this thread solved.

---

### Post by tom17 on 2009-06-23
Hi there,

I was trying to set the wallpaper too using gconftool-2. It was working when using a console inside GDM, but not from an ssh session or from cron. That is when I found your thread.

I got it working, but thought I should add that there is nothing wrong with the way you were doing it before and that there is no need to go checking nautilus, although it is also a perfectly valid method. With the original method, you do have the option of choosing which deisplay you wish to do this for, although this basic script assumes :0.0

The only problem was in the implementation of your script.

Try this instead...

**Old code:**
```
# Get dbus session for gconftool-2
ON_USER=$(cat /etc/passwd | grep :1000: | cut -d ':' -f 1)
```

Not sure why you specifically wanted the user with group id or user id of 1000, so I just will use the current user instead
[B]
Old code:[/B]
```
export DBUS_SESSION=$(grep -v "^#" /home/$USER/.dbus/session-bus/`cat /var/lib/dbus/machine-id`-0)
```
2 probs with this. First, the environment variable should be called DBUS_SESSION_BUS_ADDRESS and secondly you are setting the variable to three lines of text like this:

```
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-45v55v4v65,guid=a7857635b8778c78623f89723e986b82
DBUS_SESSION_BUS_PID=34377
DBUS_SESSION_BUS_WINDOWID=4121785

```
[B]
New code:[/B]
```
export DBUS_SESSION_BUS_ADDRESS=$(grep "^DBUS_SESSION_BUS_ADDRESS=" /home/$USER/.dbus/session-bus/`cat /var/lib/dbus/machine-id`-0 |cut -d'=' -f2-)
```

Note that this only works if the user is logged in to gnome using display :0.0

The rest was fine except the username and the environment variable setting. Alternatively, sudo is not really needed assuming you are running all of this under the same user that you are trying to change the background for.
[B]
Old code:[/B]
```
# start of gconftool command and set the desktop
sudo -u $ON_USER $DBUS_SESSION /usr/bin/gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$picsfolder$randomfile"
```

**New code:**
```
# start of gconftool command and set the desktop
/usr/bin/gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$picsfolder$randomfile"
```

So, concicely...

```
export DBUS_SESSION_BUS_ADDRESS=$(grep "^DBUS_SESSION_BUS_ADDRESS=" /home/$USER/.dbus/session-bus/`cat /var/lib/dbus/machine-id`-0 |cut -d'=' -f2-)
# start of gconftool command and set the desktop
/usr/bin/gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$picsfolder$randomfile"
```

Hope this helps.

Tom...

---

