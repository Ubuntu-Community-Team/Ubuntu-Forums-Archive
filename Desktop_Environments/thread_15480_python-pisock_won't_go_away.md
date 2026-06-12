---
title: "python-pisock won't go away"
date: 2005-02-14
forum: Desktop Environments
---

### Post by Mercyst on 2005-02-14
noob question for today, I was about to start installing the 8.8.25 ati drivers when, as I tried removing the old ones.....

 files list file for package `python-pisock' is missing final newline
Errors were encountered while processing:
 python-pisock
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

comes up.
I proceed to try and remove python-pisock anyways, as I don't use a palm device as it is....but I keep getting the same error


(Reading database ... dpkg: error processing python-pisock (--remove):
 files list file for package `python-pisock' is missing final newline
Errors were encountered while processing:
 python-pisock
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


suggestions would be wonderful. I need to get rid of this bastard before I can do anything...and no method of removal seems to be working.

Note: I am not even able to re-install the package, same error.



Ignore me, I fixed the problem myself. Managed to force remove it and get the drivers installed.

---

### Post by kamstrup on 2005-02-15
You might try "sudo dpkg --purge python-pisock"... I am no expert though, but this has worked for me before in removing damaged/weird packages.

Good luck!

EDIT:
Whoops... Just noticed the last line in your post. Gongrat's then ;-P

EDIT OF EDIT:
It is good custom to post the solution, so that others might benefit from your experiences. Cheers.

---

