---
title: "sudden login problem"
date: 2006-08-17
forum: Desktop Environments
---

### Post by tkirke on 2006-08-17
I'm suddenly having this problem after rebooting from yesterday where I get into a login loop.
I can use recovery and startx using root without a problem
but normal login does not work
I also deleted and created a new user without improvement!

Anyone else seeing this? 
Or howto fix?

---

### Post by coolclassic on 2006-08-17
The answer to first question is yes. The fix is to delete a file in your home directory and I can't remember which one. SORRY! :(

---

### Post by ajgreeny on 2006-08-17
I think it is the .ICEauthority file in your home folder that needs removing.  Try doing that in recovery mode, which you can get into and then restart.

Look at the following site where there is a peice on the possible problem and how it came about (using sudo for graphical programs?).

I quote
    *

      NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting * with your username.

rm /home/*/.{ICE,X}authority

    *

---

