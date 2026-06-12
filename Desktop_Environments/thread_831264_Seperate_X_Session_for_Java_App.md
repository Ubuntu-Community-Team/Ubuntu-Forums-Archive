---
title: "Seperate X Session for Java App"
date: 2008-06-16
forum: Desktop Environments
---

### Post by Jivicin on 2008-06-16
I'm trying to run a Java application on a separate X session and am having problems.  

What I want to do in the end is be able to run a script from the console that initiates a separate X session, and then starts my Java application.  The Java app will launch a JFrame with my window.

One of my many questions would be, what all do I need to run to get my Java app working?

Here's my existing launch config:

```

#!/bin/sh

X :3 -ac &   # Launches a new X session on display 3
cd ~/.workspace/HoD/
sleep 2   # Forces the system to have a break for 2 seconds
DISPLAY=:3 /usr/bin/metacity && ~/.workspace/HoD/HoD.sh

```

HoD.sh is a script that sets various environmental vars and launches Java.  I tried launching this with and without metacity.  It made no difference.

Any help would be appreciated!

---

### Post by Zorael on 2008-06-16
I think the error lies in your double ampersands (&&). That makes it wait for metacity to exit with the errorlevel 0 (correct?), which really isn't what you want.
```
#!/bin/sh

X :3 -ac &				# Launches a new X session on display 3
cd ~/.workspace/HoD/
sleep 2					# Forces the system to have a break for 2 seconds
DISPLAY=:3 /usr/bin/metacity &
DISPLAY=:3 ~/.workspace/HoD/HoD.sh &
```
If it doesn't work even without metacity, make it open up xterm (or gnome-terminal, or konsole, etc etc). Then run your script from there and see if it outputs anything interesting error-wise.

---

### Post by Jivicin on 2008-06-18
Thanks!  That worked perfectly.

I was just wondering if there was a preferred method of shutting down the separate X session for this?

I tried just killing the job, but that sometimes has some weird results.

---

