---
title: "how to use gnome-screeensaver-command -d (unblank screen)"
date: 2014-06-18
forum: Desktop Environments
---

### Post by Hiflux_Seven on 2014-06-18
Under 14.04 Trusty, I have the gnome screensaver set to blank the screen after 10 minutes.
Occasionally I wish to inhibit the blanking, formerly available as an option (-i) within gnome-screensaver-command tool.

Instead, I opted for a small bash script utilizing the -d (deactivate) option instead:

   #!/bin/bash
   while true
   do
           /usr/bin/gnome-screensaver-command -d
          sleep 60s
   done


Unfortunately, it doesn't seem to work.  I can run /bin/bash -x noblankscript.sh, see gnome-screensaver-command -d
executed every minute, yet the screen will still blank after 10 minutes.

What am I doing wrong??

---

