---
title: "Cron Jobs Not Running"
date: 2009-04-08
forum: General Help
---

### Post by petersm2 on 2009-04-08
I am trying to back up some data to an external hard drive. Using Grsync and Gnome-Schedule I have setup everything and each schedule task works fine when I do it manually in Gnome-Schedule. But for some reason they won't run on their own.

When I view my crontab with the terminal, I see all my grsync sessions.

I have tried adding my user to the crontab group.

I setup a test to execute at a specific time and I get this in the sys.log:
Apr  8 13:56:02 mike-inspiron /USR/SBIN/CRON[12341]: (mike) CMD (grsync -e Test >/dev/null 2>&1 #JOB_ID_12)

So, I'm guessing cron is running, and I also see it in services, but I don't see crond in the services and "service crond status" says that is doesn't recognized the service. Does crond need to be running? Is it a part of cron? I looked for  it in synaptic but couldn't find it.

I do have anacron installed if that makes any difference.

I have also tried adding DISPLAY=0.0 to the beginning of my crontab, but that did nothing as well.

I've searched this forum but none of the solutions I found worked. Anybody have any idea what's going? Also I'm using Ubuntu Intrepid, and I'm very new to linux.

---

### Post by Tony Flury on 2009-04-15
Have you tried to confirm that cron is working correctly with a very simple script which echos a line of text to a log file ?

I know it sounds very basic - but that is where i would start.

---

