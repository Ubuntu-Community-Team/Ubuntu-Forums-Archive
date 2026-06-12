---
title: "trouble creating startup script"
date: 2009-01-17
forum: General Help
---

### Post by nick_edwards on 2009-01-17
I've been trying to create a startup script which I can edit to start application at startup - load display colour profiles etc... - I created a file in /etc/init.d called startup and put in it:

#!/bin/sh -e
#
# startup.sh

# This script was created to allow executing custom commands on startup autoexec style.


zenity --warning --text="Startup script working"
xcalib /home/nick/profiles/b100t65g22.icc

exit 0

When run the script brings up a window and displays: 'Startup script working' then loads a display profile to calibrate my monitor

the script is executable and works when I execute it.

then I typed:
sudo update-rc.d startup start 99 2 3 4 5 . stop 01 0 1 6 . 
which created the symbolic links in the rc2.d etc as expected. 
Then I restarted and ... nothing????
any idea what I'm doing wrong, this thing is driving me mental

---

### Post by eightmillion on 2009-01-17
> **nick_edwards said:**
> I've been trying to create a startup script which I can edit to start application at startup - load display colour profiles etc... - I created a file in /etc/init.d called startup and put in it:

#!/bin/sh -e
#
# startup.sh

# This script was created to allow executing custom commands on startup autoexec style.


zenity --warning --text="Startup script working"
xcalib /home/nick/profiles/b100t65g22.icc

exit 0

When run the script brings up a window and displays: 'Startup script working' then loads a display profile to calibrate my monitor

the script is executable and works when I execute it.

then I typed:
sudo update-rc.d startup start 99 2 3 4 5 . stop 01 0 1 6 . 
which created the symbolic links in the rc2.d etc as expected. 
Then I restarted and ... nothing????
any idea what I'm doing wrong, this thing is driving me mental

If your script is running before X has even started then it really isn't too much of a surprise that it doesn't do anything, since you are trying to display window and recalibrate X. You need to link your script in the autostart folder of what ever environment you're running. That could be /etc/xdg/autostart/ or ~/.kde/Autostart/ or  ~/.config/autostart/.

---

### Post by lensman3 on 2009-01-17
You only want it to run in run-level 5.  Run-level 5 is when X11 is running.  All the other run-levels are with a raw text screen.

---

### Post by sedawk on 2009-01-17
You might try to start by using an existing startup script in /etc/init.d
and to copy and modify it.

See /etc/rc.local

Remember that the default PATH might be very simple, so many commands
are not found when you do not use the full path to run /usr/bin/zenity,
you might have to give "/usr/bin/zenity" in your script, not only
"zenity" (or you add "/usr/bin" to the PATH first).

---

### Post by mssever on 2009-01-18
This needs to run in a session startup script, not an init script, since most init scripts are run before X is up. You might, however, be able to play with Upstart and run your script on the "X is running" event. However, you still shouldn't count on being able to show windows on the screen.
> **lensman3 said:**
> You only want it to run in run-level 5.  Run-level 5 is when X11 is running.  All the other run-levels are with a raw text screen.
That's not correct in Ubuntu. In Ubuntu, runlevels 2-5 are identical, and Ubuntu defaults to runlevel 2. Actually, that's an oversimplification, because technically, Ubuntu doesn't have any runlevels. Ubuntu instead uses the event-based Upstart, which has events that run the rc*.d scripts and emulate runlevels.

---

### Post by nick_edwards on 2009-01-21
Thanks everyone for clearing that up for me, 
another lesson in Linux.
How great is the Ubuntu community?

---

