---
title: "Startup programs: postpone"
date: 2008-05-17
forum: Desktop Environments
---

### Post by xtreme- on 2008-05-17
Hi,
I'm using Ubuntu (GNOME), and I have added a few startup programs (System->Preferences->Startup Programs).
This works nicely, but the problem is that it of course takes more time before I may use the computer when it boots up.

But it does not really matter if these programs start immediately after boot, or maybe 2 minutes later (the programs are e.g. instant messaging, feed reader, etc. - just things to keep in the background).
And I don't want to wait one extra minute just to get these loaded.

So what I thought would be better is if it was possible to "postpone" the execution of these programs: to have some daemon watch e.g. hd/cpu usage and start the programs when the user is using little of the computer resources (maybe she has started browsing the web or is writing a document?). Or maybe just start them two minutes after GNOME is loaded, instead of letting the user wait for them to start.

Do any of you have suggestions for setting this up? Maybe a bootscript that adds a cron job two minutes ahead of current time? I thought it would be nice to have a way to do this graphically, for instance check a box called "low priority" or "postpone" in the "Startup Programs" dialog box, as I think this could be a nice functionality for many people.. (It should not be GNOME-specific, though.)

What do you think? Is it a good idea?

---

### Post by Xiong Chiamiov on 2008-05-18
Though it wouldn't be through the GUI, you could change/add the startup scripts in /etc/init.d and add either the wait or sleep commands.  Wait delays until background processes have finished, and sleep will wait a given number of seconds.  If you need help with doing this, I think I can manage if you give me an example app.

---

### Post by xtreme- on 2008-05-18
Adding a bootscript seems like the way to go right now.. I think I'll be able to google for an example, but thanks anyway. ;)

But I'm interested in knowing your opinions on this, do you think it would be useful for you? I was thinking about suggesting this as a feature to be added to the desktop environments (I read somewhere that everyone may suggest new features for Ubuntu).

So, would any of you find this useful / have any opinions on this?

---

### Post by wyhog on 2008-05-18
A selectable delay like that might help me? I've been trying to get a python/tk program to run at start up by using Sessions. It won't work. I can get java programs and plain python programs (non tk windows) to start and run that way but no python/tk program will do it. I am wondering if a delay before starting might help? 

(The python/tk programs run ok if manually started by doubleclicking them in Nautilus.)

Wyhog

---

### Post by Xiong Chiamiov on 2008-05-18
> **xtreme- said:**
> Adding a bootscript seems like the way to go right now.. I think I'll be able to google for an example, but thanks anyway. ;)

But I'm interested in knowing your opinions on this, do you think it would be useful for you? I was thinking about suggesting this as a feature to be added to the desktop environments (I read somewhere that everyone may suggest new features for Ubuntu).

So, would any of you find this useful / have any opinions on this?

Sure, I could see a use for it.  Less so than in Windows, though, where I always had so much crap loading that I had to prioritize security apps first or else everything would get bogged down and take longer overall.

> **wyhog said:**
> A selectable delay like that might help me? I've been trying to get a python/tk program to run at start up by using Sessions. It won't work. I can get java programs and plain python programs (non tk windows) to start and run that way but no python/tk program will do it. I am wondering if a delay before starting might help? 

(The python/tk programs run ok if manually started by doubleclicking them in Nautilus.)

Wyhog

If you can figure out how to run it in a terminal window, then we can get it autostarted.  I don't know much about TK (I'm just starting to learn Python, and I won't be focusing on GUI apps), but it might be something along the lines of
```

python [path to app]

```

---

### Post by wyhog on 2008-05-19
>If you can figure out how to run it in a terminal window, then we can get it autostarted. 
... it might be something along the lines of ... python [path to app]

I can run it fine from a terminal. I just can't get it to run from Sessions Startup, that is why I thought his idea of a delay might help.

Wyhog

---

### Post by sdennie on 2008-05-19
Rather than starting apps directly, you could create a script called something like delayed-load.sh that looks like this:

```

#!/bin/bash

sleep 60

if ! pgrep $1 > /dev/null ; then
    exec $@
fi

```

That will wait for 60 seconds and then, if the command hasn't already been started by the user, run it.  Just prefix all the things you want to be delayed with the script in System->Preferences->Sessions.

---

### Post by wyhog on 2008-05-19
:cool:
Wow! That works. Starting the "delay" shell script in Sessions instead of directly starting the python/tk program in Sessions works. It will now run my program at startup. Well a few seconds after startup.  ;)

Thank you, VOR.

I still think the fact that Ubuntu will not run a python/tk or a pythom/gtk program directly from Sessions without this delay work-around is a bug though.

Wyaak

---

