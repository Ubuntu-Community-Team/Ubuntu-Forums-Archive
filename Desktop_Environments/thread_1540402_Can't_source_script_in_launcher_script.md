---
title: "Can't source script in launcher script"
date: 2010-07-27
forum: Desktop Environments
---

### Post by dansmith on 2010-07-27
I've got a script, "setup", that sets some environment variables.  I have another script, "launch", that launches a program for me.  A launcher on my menu panel is set to run command "launch".

Here's what the text of "launch" looks like:

source setup
export FOO=$VAR_FROM_SETUP
gui-program

If I run this from the launcher, the program sees an empty string for FOO.  If I run it from a terminal, the program sees a correct value for FOO.

Why the discrepancy?  Is there a workaround that will allow a launcher to set variables via "setup" before running my program?

---

### Post by dansmith on 2010-07-28
Solved by forcing the script to launch under bash (doesn't work under sh, apparently):

#!/bin/bash
source setup
export FOO=$VAR_FROM_SETUP
gui-program

---

