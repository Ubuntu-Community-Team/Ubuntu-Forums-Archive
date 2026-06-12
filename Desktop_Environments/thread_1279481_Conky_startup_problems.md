---
title: "Conky startup problems"
date: 2009-09-30
forum: Desktop Environments
---

### Post by rm06 on 2009-09-30
My conky configuration which has been working fine for quite some time is now not auto starting. I did recently "downgrade" from 64-bit 9.04 to 32 as it was simply causing too many headaches.

I have a .conky_start.sh script:

#!/bin/bash
sleep 30 && conky;
chmod a+x .conky_start.sh

And I'm referencing the location of this file in my startup sessions manager. I can manually execute the operation from the command line via either "conky" or "sh .conky_start.sh" without issue.

From the daemon.log file I found the following:

Sep 30 19:21:17 MyComputer x-session-manager[3506]: WARNING: Application 'compiz.desktop' failed to register before timeout 

Sep 30 19:21:20 MyComputer x-session-manager[3506]: WARNING: Could not launch application '.conky_start.sh.desktop': Unable to start application: Failed to execute child process "/home/me/.conky_start.sh" (Permission denied) 

I've changed the permissions on the desktop file to both root and myself through gedit and using chown, neither of which results in any difference and I still receive the errors. I've googled the errors and I've found some bugs for compiz though they don't seem to relate to the issues I've been experiencing.

Obviously this is a minor inconvenience having to start from the terminal as it is usually up anyway, though I'd like to understand and learn how to fix these "bugs" as they arise.

---

