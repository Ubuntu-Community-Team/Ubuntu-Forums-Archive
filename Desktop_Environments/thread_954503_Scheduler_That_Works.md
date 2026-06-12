---
title: "Scheduler That Works????"
date: 2008-10-21
forum: Desktop Environments
---

### Post by Quarkrad on 2008-10-21
I have a simple script that copies files from one folder to another

 /usr/bin/grsync -e default

I can get this to work if run in terminal - I have created a task in the default Scheduled Tasks under System/Preferences and can execute the task if I click on the *Run task* icon.  Great.  But ......... if I try and automate this task (e.g. every 20 mins, or 1 hour  or as a one off once only task at a specific time) it never works.  I have been trying for days to automate this task but failed - using either Kcron or Scheduled Task.   As somebody new to Ubuntu I assume you set a scheduled task and it will automatically kick off - I'm not sure whether I'm doing something wrong somewhere or wasting my time because the functionality does not work.

---

### Post by jongkind on 2008-10-21
Kalarm can do this job for you. It can execute scripts (also recurring). Kalarm is in the repositories. Don't forget to put it in 'system-preferences-sessions' also after you installed it. By doing that it is automatically started when you log-in.

---

