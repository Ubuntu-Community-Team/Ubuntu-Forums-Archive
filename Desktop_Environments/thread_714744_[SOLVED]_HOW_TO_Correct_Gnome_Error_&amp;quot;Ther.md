---
title: "[SOLVED] HOW TO: Correct Gnome Error &amp;quot;There was an error starting the GNOME Settings"
date: 2008-03-04
forum: Desktop Environments
---

### Post by arimaniac on 2008-03-04
**This post could be related to an Ubuntu bug filed at**: [http://bugzilla.gnome.org/show_bug.cgi?id=395488](http://bugzilla.gnome.org/show_bug.cgi?id=395488) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
Hi everybody...

This how to provides step by step instructions on resolving
a known error in the Gnome Settings Daemon.

**PROBLEM:**

On a system startup the following message appears in a dialog box:
Also that all desktop settings are missing(colors, fonts, styles etc...)

> 
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, 
the message bus security policy blocked the reply, the reply timeout expired, 
or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

**REMARKS:**

This HOW TO is written and tested by me but some code was written by iammeagain.
This mod is actually a workaround that generally adds error 
controlling using a temporary file as a flag and its pretty good actually.
It has been tested on two Ubuntu 7.10 and one 7.04 and works perfectly.

**SOLUTION:**

Step 1:

Type in terminal:
```
sudo gedit /etc/X11/Xsession.d/55gnome-session_gnomerc
```

The following file appears:

```
# If we are running the GNOME session, source ~/.gnomerc
BASESTARTUP=`basename "$STARTUP" | cut -d\  -f1`
if [ "$BASESTARTUP" = gnome-session -o \
	\( "$BASESTARTUP" = x-session-manager -a \
	"`readlink /etc/alternatives/x-session-manager`" = \
		/usr/bin/gnome-session \) ]; then
  GNOMERC=$HOME/.gnomerc
  if [ -r "$GNOMERC" ]; then
    . "$GNOMERC"
  fi
fi
```

STEP 2:
Add two lines of code as indicated in 
**BOLD-ITALIC AS THEY APPEAR below and SAVE**:

THIS IS THE CODE:
(1) rm -f /tmp/session-is-gnome
(2) touch /tmp/session-is-gnome

AND ITS PLACED **EXACTLY** LIKE THIS:

```

# If we are running the GNOME session, source ~/.gnomerc
***rm -f /tmp/session-is-gnome***
BASESTARTUP=`basename "$STARTUP" | cut -d\  -f1`
if [ "$BASESTARTUP" = gnome-session -o \
	\( "$BASESTARTUP" = x-session-manager -a \
	"`readlink /etc/alternatives/x-session-manager`" = \
		/usr/bin/gnome-session \) ]; then
  GNOMERC=$HOME/.gnomerc
  if [ -r "$GNOMERC" ]; then
    . "$GNOMERC"
  fi
***  touch /tmp/session-is-gnome***
fi

```

Step 3:


Type in terminal:
```
sudo gedit /etc/X11/Xsession.d/99x11-common_start
```

The following file appears:
```

# $Id: 99x11-common_start 305 2005-07-03 18:51:43Z dnusinow $

# This file is sourced by Xsession(5), not executed.

exec $STARTUP

# vim:set ai et sts=2 sw=2 tw=80:
```

Step 4:

Put a # (hash) in front of the "exec $STARTUP" line 
as shown below: (making it a comment).

```

# $Id: 99x11-common_start 305 2005-07-03 18:51:43Z dnusinow $

# This file is sourced by Xsession(5), not executed.

***#exec $STARTUP***

# vim:set ai et sts=2 sw=2 tw=80:

```

Step 5: 
Add the following code to the bottom file and SAVE:

```

if [ -f /tmp/session-is-gnome ]; then
  exec /usr/bin/dbus-launch $STARTUP
else
  exec $STARTUP
fi
```

The new file should be like this:

```
# $Id: 99x11-common_start 305 2005-07-03 18:51:43Z dnusinow $

# This file is sourced by Xsession(5), not executed.

***#exec $STARTUP***

# vim:set ai et sts=2 sw=2 tw=80:

[B][I]if [ -f /tmp/session-is-gnome ]; then
  exec /usr/bin/dbus-launch $STARTUP
else
  exec $STARTUP
fi
```[/I][/B]

Step 6:
Reboot your PC
DONE :)

UPDATE:

When upgrading to Hardy this patch has to be reapplied although
do note that the bug did not appear again in my PC. 

Comments - questions welcome!!!

---

### Post by abyssius on 2008-03-04
Thank You! Thank You! Thank You!

I've been puzzling over this for week now. I used to be able to correct it by manually restarting dbus and hal - then rebooting. However, this might not have had anything to do with the problem.

FYI, this only happened to me when I booted the 2.6.22-14-rt real-time kernel (which I added over a generic install). If I booted  the 2.6.22-14-generic kernel, the problem seemed to go away.

I'm not yet versed enough in Linux to understand the "how" of the fix, but I'm extremely gratified that you took the time to post this solution.

---

### Post by RgnKjnVA on 2008-03-04
well, I don't get the Gnome Settings Daemon error anymore but I also can't seem to get my desired theme to display and I'm getting an error message at start up saying something about a mismatch between the Gnome and X session keyboard config.

I'm running Gutsy

---

### Post by mtbsoft on 2008-03-05
I only get this error about once a fortnight but I might give this a go and report back if I get it occur again.  

Cheers

---

### Post by Th3Professor on 2008-03-05
I was getting the same error message. The solution provided above is working (so far, and hopefully permanently). Thanks for the howto. :)

I came across some similar threads:

[http://ubuntuforums.org/showthread.php?t=339491](http://ubuntuforums.org/showthread.php?t=339491)

[http://ubuntuforums.org/showthread.php?t=553094](http://ubuntuforums.org/showthread.php?t=553094)

...and some bug links...

[http://bugzilla.gnome.org/show_bug.cgi?id=395488](http://bugzilla.gnome.org/show_bug.cgi?id=395488)

[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/138277](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/138277)

(Previous versions of Ubuntu but perhaps helpful info for someone.)

Since this thread provided an immediate solution I didn't bother looking any further into those other threads/links but thought I'd put them in here if anybody wants to use them for additional reference.

---

### Post by arimaniac on 2008-03-14
to Th3Professor  : thanks for the links .... will check them out and post any updates...

to RgnKjnVA::  

NO THEME??? This is odd.... 
NOT LINKED TO THE SETTINGS DEAMON IF YOU APPLIED THIS...
**NOT LIKED FOR SURE**....

Hope this helps...


Good luck

---

### Post by doctorbighands on 2008-03-17
Incredible.

arimaniac, you're my own personal jesus for the day. I can't thank you enough.

---

### Post by arimaniac on 2008-03-17
To : doctorbighands  

You're welcome ...

You can give thanks by constantly 
contributing to the Ubuntu community..

**LETS MAKE LINUX BETTER!!!**

---

### Post by Nidding on 2008-03-19
Thank you so much. This has been bugging me since I installed Ubuntu Studio.

---

### Post by Th3Professor on 2008-03-20
> **Nidding said:**
> Thank you so much. This has been bugging me since I installed Ubuntu Studio.

...same with my studio install... hopefully those in charge of Ubuntu Studio will fix this in an upcoming release.

---

### Post by mtbsoft on 2008-04-10
Unfortunately, I have to report that this error hit me again last night.  That said, it is the first time in about five weeks but it would appear there is still a way for the problem to reappear on occasion.

On this occasion it was a slightly different error to the usual though, this time relating to a socket timeout (sorry, didn't have the opportunity to make a proper record)..

---

### Post by joarc on 2008-04-10
Ok, I typed into the terminal as stated but all that comes up is blank, there is no code written there, just a blinking cursor??  The file open says it's 55gnome-session_gnomerc (/etc/Xll/Xsession.d) - gedit.  I can type in it but thats it.  Ubuntu 7.10. I looked around, thought maybe I'd have to change a view or something but no go. HELP :)

---

### Post by arimaniac on 2008-04-11
OK THIS IS ODD....

WELL NO IDEAS FROM ME.....


ARE YOU SURE YOU ARE USING AN X11 GUI????

A SILLY QUESTION BUT THATS WHAT I CAN COME UP WITH....
:p

---

### Post by arimaniac on 2008-04-11
> **mtbsoft said:**
> Unfortunately, I have to report that this error hit me again last night.  That said, it is the first time in about five weeks but it would appear there is still a way for the problem to reappear on occasion.

On this occasion it was a slightly different error to the usual though, this time relating to a socket timeout (sorry, didn't have the opportunity to make a proper record)..


SOCKET TIMEOUT????

COULD YOU POST SOME TERMINAL OUTPUT TEXT.. 
OR SOME MSGBOX TEXT THAT DESCIBES THIS???

THX

---

### Post by joarc on 2008-04-11
I gave up... too many other problems. So I'm doing a reinstall.  Thanx! :)

---

### Post by mtbsoft on 2008-04-13
> **arimaniac said:**
> SOCKET TIMEOUT????

COULD YOU POST SOME TERMINAL OUTPUT TEXT.. 
OR SOME MSGBOX TEXT THAT DESCIBES THIS???

THX
Unfortunately, I was late to get somewhere and didn't have time to make a note of the output, I shall if/when it happens again.  All I do recall was that it was different from the usual message and that may be why it came up.  I should add that five weeks without the usual error was good for me so I'm still happy with the fix.

I'll report if I get it again.

---

### Post by garyed on 2008-04-19
Well the fix worked for a while in Gusty but now its back again.
I double checked all the files & they look right.
> 
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

---

### Post by mtbsoft on 2008-04-28
> **garyed said:**
> Well the fix worked for a while in Gusty but now its back again.
I double checked all the files & they look right.

Yep, had it again myself just now, the exact same message as yourself this time.  Likewise all the files appear correct.

Still about to install Hardy in a separate partition to play a while before committing so might not have to worry about it again soon.

---

### Post by Frogster on 2008-07-19
How do I enter this code into the terminal when I cant get past the error message?

---

