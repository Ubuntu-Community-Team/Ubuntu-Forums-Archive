---
title: "No Directory, Logging in with HOME=/"
date: 2011-03-05
forum: Desktop Environments
---

### Post by hateborne on 2011-03-05
[B]No Directory, Logging in with HOME=/
Cannot execute /bin/bash: Permission Denied
[/B]

I was trying to setup ePSXe. I was supposed to enter > export EPSXE='/usr/local/games/epsxe' but somehow screwed it up. After entering the typo'ed command ALL icons vanished, all programs refused to activate, and then locked up. After restarting I was met with command line only.

I am able to log in with root, can access all the files on the hard drive. However, I cannot find where the "export VAR=" actually leads out. I believe that I might be able to save the installation of Linux if I could manually undo the changes.

I've spent 3h finding tidbits of info, but nothing overly useful. Any pointers would be very useful and greatly appreciated.

If nothing can be done to rebuild this file(s), is there anyway to save the information on the system (reinstalling Ubuntu over the old one without destroying any of the information, as such will probably destroy my chances of passing this semester)?

-Hate

---

### Post by rosencrantz on 2011-03-05
Hi hateborne,
I don't think that exporting a string variable like that can screw up your home permissions like that (did you use these instructions?[http://www.psy-q.ch/gaming/linux/epsxe_howto/](http://www.psy-q.ch/gaming/linux/epsxe_howto/)), especially as definitions like that are temporary and should be unset when the bash session or the whole machine is shut down anyway. You can try unset EPSXE, but I don't think it will help.
Try checking ownership and permissions for /home and /bin (ls -la), it should be 
drwxr-xr-x  root root 
for bin and 
drwxr-xr-x <youruser> <youruser> 
for /home/<youruser>. If there's something wrong, chmod, chgrp and chown should do the trick.
Also check ~/.bashrc and ~/.bash_history for suspicious statements (or post them here :))

Cheers
rosencrantz

---

### Post by hateborne on 2011-03-08
Thank you for the reply. Somehow the permissions are all kinds of ridiculous. Somehow the "root" user can only be accessed via a recovery console, my account is loading again and the GUI login will partially load (as in the Ubuntu logo, the slightly homo-erotic color spray, and the neat toolbar at the bottom).
 
I am going to have to try data backup and blow it. sudo also doesn't work, and the environment, .bashrc, etc etc all show normally. 
 
Somehow I have fubar'ed into epic failure. Thank you all the same.
 
I've just got to figure out how to backup my VBox machines where they will boot normally after being recopied. If my VBox machines fail, I'm insta-failing one class this semester :-\
 
-Hate

---

### Post by rosencrantz on 2011-03-10
I've had no trouble with migrating VBox virtual partitions between systems, so I guess you'll be all right :-)

---

