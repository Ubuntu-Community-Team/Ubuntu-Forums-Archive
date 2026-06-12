---
title: "why mouse auto activated!"
date: 2006-08-09
forum: Desktop Environments
---

### Post by say2sky on 2006-08-09
When mouse cursor stop at some place for a few seconds, it will automaticly activate the object it point to such as links or title bar. This happen in terminal, editor and browser. 


What happen to my system? I have tried to use chkrootkit and clamscan but no any malware can be found. 

Please help to give some suggestion to solve this strange thing in Ubuntu 6.06.

---

### Post by kerry_s on 2006-08-09
Check your mouse settings, turn off activate on hover to stop it.

---

### Post by fragos on 2006-08-09
That is happening because your system is configured for "focus" to follow the cursor.  I believe the configuration editor can fix this.  Go to /, apps, metacity, general, focus_mode.  The default value is "click" with "sloppy" and "mouse" as the other options.  You want "click"

---

### Post by say2sky on 2006-08-10
[COLOR="Blue"]That is happening because your system is configured for "focus" to follow the cursor. I believe the configuration editor can fix this. Go to /, apps, metacity, general, focus_mode. The default value is "click" with "sloppy" and "mouse" as the other options. You want "click"[/COLOR]

Thanks!
My configuration for focus_mode is already set to "click" but problem is still there!

---

### Post by say2sky on 2006-08-10
Thanks all for help! I have gotten the cause for this strange thing.  Because I run Drupal on my Ubuntu machine, the cron run cron.php every hour to do the indexing for my website and it cause mouse automatically activate and move the active input point on the terminal to the mouse cursor position. 

I think it is the cause but I don't know why. Perhaps bug!

---

