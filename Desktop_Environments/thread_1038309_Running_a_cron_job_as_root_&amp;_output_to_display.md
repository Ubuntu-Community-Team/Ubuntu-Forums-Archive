---
title: "Running a cron job as root &amp; output to display 0 where other user logged in"
date: 2009-01-12
forum: Desktop Environments
---

### Post by feizex on 2009-01-12
Hi Guys,

It took me quite a while to figure this out and I thought I would share.

The scenario is this: 
I want to run a dial command for ekiga at a scheduled time. Since Ekiga is an xwindows app (I am still new, correct me if this is incorrect terminology) it will not execute from tty unless display is specified. BUT since I have to run the command as root and root is not logged into that display, the command does not execute. 

It instead gives the error:
[B]No protocol specified
cannot open display: 0[/B]


The answer is this: I need to set display# AND authorise root to connect to that xwindow session.

Here's what I found after lots of googling and also trial and error.

Edit root crontab with following command.
**sudo crontab -u root -e**

Add the following line (modify date/time currently 7:30am every day and COMMAND)
**30 7 * * * export DISPLAY=:0 && xauth merge /var/lib/gdm/:0.Xauth && COMMAND**

Here is my understanding of what this does...

The export sets an environment variable that the command looks at to see which x display to use.

The xauth merge command is opening the authorisation file for display 0 and copying that into root's xauth file. This gives root authority to that xwindows session.

Crontab can now run your command as root with access to connect to current xwindows display 0. ENJOY! :popcorn:

Regards,
Feizex.

---

