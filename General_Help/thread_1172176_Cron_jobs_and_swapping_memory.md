---
title: "Cron jobs and swapping memory"
date: 2009-05-28
forum: General Help
---

### Post by vanderkerkoff on 2009-05-28
Hello everyone

I'm using Ubuntu 8.04 server and I'm running into a problem.

I have a rake task that grabs alot of data out of a csv file and imports it into our mysql database.  When I run the rake task from in the console the amount of memory needed to complete the task exceeds that available memory and swapping occurs to complete the task.

When I run this job from within cron, at the moment when swapping needs to occur to complete the task the task fails and the swapping does not occur.

It's as if I need to tell cron to allow memory swapping.

Has anyone seen anything like this before or have any ideas on how I tell cron to allow memory swapping to complete it's tasks?

All help is greatly appreciated.

---

