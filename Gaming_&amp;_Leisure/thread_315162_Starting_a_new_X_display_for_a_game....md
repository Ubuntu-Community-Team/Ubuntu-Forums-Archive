---
title: "Starting a new X display for a game..."
date: 2006-12-08
forum: Gaming &amp; Leisure
---

### Post by SBFC on 2006-12-08
Hello all. I was wondering if anyone new how to launch a game with a new display so that while in game you could switch back to your other display. I remember reading something about it a while back but now I can't seem to locate the source.

Just want a separate display running Wolf:ET while I play.

Thanks.

---

### Post by Drezliok on 2006-12-08
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

The script there can be adapted for that purpose.

---

### Post by SBFC on 2006-12-08
Many thanks.

---

### Post by SBFC on 2007-03-26
When attempting to start a new x session for games I receive the following errors:

```
xauth:  error in locking authority file /home/oblivion/.Xauthority
xauth:  error in locking authority file /home/oblivion/.Xauthority
xauth:  error in locking authority file /home/oblivion/.Xauthority
xauth:  error in locking authority file /home/oblivion/.Xauthority
X: user not authorized to run the X server, aborting.
xinit:  Server error.
xauth:  error in locking authority file /home/oblivion/.Xauthority
Couldnt get a file descriptor referring to the console

```

Could anyone shed some light on this?

---

### Post by hikaricore on 2007-03-26
Use **sudo**. **gksudo**. or **kdesu** to launch the new X session?

---

### Post by SBFC on 2007-03-26
This one's a real bugger.

Not that I'm opposed to starting a new session with root, but you should be able to do it as a normal user. Take vncserver for example, run it as a user, and a new display is created on :1.

Meh.

---

### Post by hikaricore on 2007-03-27
I can't remember where, but somewhere there is a setting to allow X to be started by a normal user.  >.<

I just never worried enough to find out.

---

### Post by SBFC on 2007-03-27
Well, if you change the line ```
allowed_users=console
``` in the /etc/X11/Xwrapper.config file to ```
allowed_users=anybody
``` you can launch another X session.

Only problem I'm having now is once the second X session is launched, when I switch back to display :0 via Alt+Ctrl+F7 my session is foobarred. Just a black screen with a moving cursor. Then if I try and go back to screen :1 after that via Alt+Ctrl+F8 that too is a black screen with a moving cursor. Have to restart gdm to fix it.

---

### Post by hikaricore on 2007-03-27
Hmm... i've never had that problem.  Maybe try disablling your screensaver?

Atleast it will rule that out as a possibility, unless it is right after launching, then I'm not really sure what it could be.

-

btw are using the "DISPLAY=:3"?  because for me that's ctrl+alt+f9 O.o

---

### Post by SBFC on 2007-03-27
No, I'm using :1. And the screen going black is happening right after I lanuch the new session and attempt to switch back.

Wonder if my vid card could somehow be behind it. Hope not. :P

---

### Post by SBFC on 2007-03-27
Well, I found out what was causing the X server to stop responding/show up black when switching between displays :0 and :1. It's freakin Beryl. 

Found out by accident. Switched to tty1 and couldn't get back to X. Disabled Beryl, ran ET on display :1 and switched back to :0 no problems.

Funny thing, the whole reason I wanted to run my games on a separate X server was because I was using Beryl. Turns out that isn't going to work. :(

EDIT:

Almost forgot, just in case any one else was interested in this. Here's what I use to run Enemy Territory on a separate X display:

```

#!/bin/bash

X :1 -ac &
XPID=$!
sleep 2
DISPLAY=:1 /usr/local/bin/et-start
sleep 1
kill $XPID

```

Based on the WoW howto, and the extra stuff is what I found while doing some extensive Google searches. It'll kill the newly created X display after you exit the game.

And I also had to change /etc/X11/Xwrapper.config from 

```

allowed_users=console
nice_value=0

```

to

```

allowed_users=anybody
nice_value=0

```

---

### Post by jpkotta on 2007-03-28
This is the alias I use to start Tremulous.  No modifications of config files needed. However, I must start from the console (the way I have it, it will not start a new server if started from an X session).
```
alias tremulous='if [[ -z $DISPLAY ]] ; then startx /usr/local/bin/tremulous -- :1 ; else /usr/local/bin/tremulous ; fi &'
```
You may like to add a '>/dev/null' to suppress all the junk that every game I've ever seen spits out to stdout.  BTW, I've found that I need the full path to start an X client directly from startx.

---

### Post by aidanr on 2007-03-28
> **SBFC said:**
> Well, I found out what was causing the X server to stop responding/show up black when switching between displays :0 and :1. It's freakin Beryl. 

Found out by accident. Switched to tty1 and couldn't get back to X. Disabled Beryl, ran ET on display :1 and switched back to :0 no problems.

Funny thing, the whole reason I wanted to run my games on a separate X server was because I was using Beryl. Turns out that isn't going to work. :(

you can switch to another tty, login and killall beryl, then switch back to your desktop and reload beryl from the systray icon, pretty annoying bug though

---

