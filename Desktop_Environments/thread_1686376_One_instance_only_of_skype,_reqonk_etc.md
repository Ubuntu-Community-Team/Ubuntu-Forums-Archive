---
title: "One instance only of skype, reqonk etc"
date: 2011-02-12
forum: Desktop Environments
---

### Post by P4man on 2011-02-12
Hi,

Is there a way to prevent spawning multiple instances of apps like skype, firefox etc ? I want the plasma thingy to open existing instances if one is already running.

Reason: Im setting up a machine (eeepc 900) that will be shipped abroad to pc-illiterate family. Its going to be used for skype mainly, and Im trying to configure it so its as simple as possible. Any other tips welcome.

---

### Post by Eager1 on 2011-06-01
Yes, I am in the same boat.
My family is limited with computer skills and the multiple instances of Skype is just an unexpected behavior. Re-training is not an option :-)

If anyone has a solution, please share.

Thank you.

---

### Post by Zorael on 2011-06-01
You can accomplish this with scripts.
```
#!/bin/bash

# Note: exclamation marks are tricky so put those in single quotes; '!'

PROGRAM=**"Skype"**             # human readable application name (for error message)
PROCESS=**"skype"**             # process name for matching
EXECUTABLE=**/usr/bin/skype**   # path to executable for starting when not running
TIMEOUT=5                   # error message timeout
TITLE="Hey, listen"'!'      # error message title

if [ ! "$(pidof $PROCESS)" ]; then
    # application not running
    $EXECUTABLE &
    disown $!
else
    # application running
    kdialog --title "$TITLE" --passivepopup "<b>$PROGRAM</b> is already running"'!' $TIMEOUT
    [COLOR="Red"]# dbus call to raise window goes here after replying to this thread and teaching me how[/COLOR]
fi
```
I looked through KWin's dbus interface but I couldn't find any way to raise a specific window (by name or by process id).

Try saving that as a script and make it executable. See if it works. You can just replace occurences of Skype there with rekonq if the script seems sound.

You can even make the script generic where it takes those strings (application name etc) from commandline arguments.

```
#!/bin/bash

if [ ! "$1" ] || [ ! "$2" ] || [ ! "$3" ]; then
    echo "usage: $0 **[application name] [process name] [path to executable]**"
    echo "use quotes to encase words"'!'
    exit 1
fi

# Note: exclamation marks are tricky so put those in single quotes

PROGRAM="$1"                # human readable application name (for error message)
PROCESS="$2"                # process name for matching
EXECUTABLE="$3"             # path to executable for starting when not running
TIMEOUT=5                   # error message timeout
TITLE="Hey, listen"'!'      # error message title

*<rest of script identical>*
```
Then edit your Skype/rekonq/etc launchers to each run that script but with different arguments.
```
$ ~/bin/startunique Skype skype /usr/bin/skype
$ ~/bin/startunique rekonq rekonq /usr/bin/rekonq
$ ~/bin/startunique "A long application name" processname /usr/bin/youknowthedrillbynow
```

And do tell me if you know of a neater way to use exclamation marks in bash. >.<

---

