---
title: "nohup command"
date: 2009-02-14
forum: General Help
---

### Post by dstein on 2009-02-14
I read about the nohup command here: [http://ubuntuforums.org/showthread.php?t=737065](http://ubuntuforums.org/showthread.php?t=737065). Among other things, it allows a process to be started from a shell, and remain open once that shell is closed. In my testing, it worked with all the programs I tried except emacs. Any idea why nohup does not work with emacs? Thanks.

---

### Post by cmnorton on 2009-02-14
Search through your logs (/var/log messages and syslog). Might be a bug in emacs.

[http://www.gnu.org/software/emacs/manual/html_node/emacs/Checklist.html](http://www.gnu.org/software/emacs/manual/html_node/emacs/Checklist.html)

---

### Post by dcstar on 2009-02-14
> **dstein said:**
> I read about the nohup command here: [http://ubuntuforums.org/showthread.php?t=737065](http://ubuntuforums.org/showthread.php?t=737065). Among other things, it allows a process to be started from a shell, and remain open once that shell is closed. In my testing, it worked with all the programs I tried except emacs. Any idea why nohup does not work with emacs? Thanks.

Do all the other programs use the X system?

---

### Post by dstein on 2009-02-14
yeah (e.g. firefox)

---

