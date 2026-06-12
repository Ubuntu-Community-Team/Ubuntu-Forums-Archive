---
title: "CRON export DISPLAY error"
date: 2020-01-19
forum: Desktop Environments
---

### Post by donporjr on 2020-01-19
Wondering about the error below, and how to stop it.

I don't have nutty installed, but this error crops up every hour

Cron <xxx@abcdefg> export DISPLAY=:0 && /usr/bin/nutty --alert

/bin/sh: 1: /usr/bin/nutty: not found


Don

---

### Post by TheFu on 2020-01-19
crontabs can be located in about 6 different places.  If it is really hourly, exactly, then I'd start by looking in the cron.hourly directory inside /etc/.  grep all those files for nutty.

FYI, cron doesn't have a session so attempting to have cron send anything to a DISPLAY server is a terrible idea. Hopefully, it is blocked by the wimpy security around both Wayland and X11 servers.

---

### Post by donporjr on 2020-01-20
Thanks for the response!

grep provides 0 nutty results

---

### Post by TheFu on 2020-01-20
Look in the other locations where cron might be.  The cron manpage lays out where those are.

Always show the command, options and output.  Otherwise, nobody can fix issues, if there are any.

---

### Post by donporjr on 2020-01-20
I may have found the entry in

/var/spool/cron/crontabs/user

I'll update once I have a result

---

### Post by TheFu on 2020-01-20
That's the area that **crontab -e** will edit, assuming you are logged in as "user".  Just run exactly that command which should load the file into nano so you can edit it.  

Either comment out the line with a # character at the beginning or delete the line. I'd comment it out for a few weeks. See how that goes.

---

### Post by donporjr on 2020-01-21
Looks like /var/spool/cron/crontabs/user

was the issue......

The error emails have stopped. Thanks for  the help

Don

---

