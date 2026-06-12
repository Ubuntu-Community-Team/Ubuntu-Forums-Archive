---
title: "[SOLVED] FreeNX / NoMachine automatic session start on boot - and variables from insi"
date: 2009-01-09
forum: Desktop Environments
---

### Post by karatefish on 2009-01-09
So I'm using NoMachine free version to run remote sessions on my ubuntu box at the moment, and I think it's great. I've got 2 questions about possibly improving my setup that I haven't found any reference to in my searches so far:

1. Is it possible to set up either NoMachine or FreeNX to automatically start a disconnected user's session on boot, rather than having to manually log in from the client program the first time and disconnect?

2. Is there any way to tell from within the desktop environment whether it's running on a physical screen or an NX session? (to autostart programs in the session without running duplicates when you log in on the physical screen, things like that)

My aim is to be able to autostart graphical programs on boot, without having to use the physical login. Anyone done anything like this before?

---

### Post by karatefish on 2009-01-10
Hmmm.. Ok, it seems to be working, but it's an ugly, ugly hack at the moment. If anyone has a better solution, I'd love to hear it.

1. Unattended session start:
So I saved the password on an existing session, so that it can be started unattended. Then I created a shell script to start nxclient when gdm starts, and then kill it once it's had time to start properly.
```
#!/bin/bash
if [ "`pgrep nxssh`" == "" ]; then
  echo "No running NX session found - starting a new one.";
  /usr/NX/bin/nxclient --session /home/user/.nx/config/SavedSession.nxs
  nx_session_file=`ls -trd /home/user/.nx/S*/session | tail -n1`
  sleep 6
  kill `grep pid $nx_session_file | cut -d"'" -f2`
else
  echo "Running NX session found, skipping start";
fi;
```
The sleep is necessary - nxclient drops back to the command line once it's started the display, but if you don't give it time to start the desktop environment properly it doesn't finish once the display window is killed. Slow machines might need a longer wait.

Also, you need to check for currently running nx sessions, because otherwise it results in a constant restart of gdm.

I then added that script to run at the start of the /etc/gdm/Init/Default file, like so:
```
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

# Start disconnected NX session
/home/user/start_unattended_nx_session
```


2. Run programs for unattended session only:
This can be done by the DISPLAY variable. A local screen will have DISPLAY=:0.0 or so, whereas the nx session currently has DISPLAY=:1174.0

Create a script something like this:
```
#!/bin/bash

if [ $DISPLAY == ":0.0" ]; then
  echo "Local display";
else
  echo "Remote display";
  deluge &
fi
```
and you can enter any commands to be run on either a local login or a remote session start. 

This can then be set to run on login by going to System->Preferences->Sessions and adding it to the startup program list.

Can anyone think of a more elegant way to do it?

---

### Post by hbradlow on 2011-11-25
Did you find a more elegant way of doing this?

What do you mean by "saved the password on an existing session" - how did you do this?

---

### Post by overdrank on 2011-11-25
Hi and please start a new thread with your issue. Thread closed. :)

---

