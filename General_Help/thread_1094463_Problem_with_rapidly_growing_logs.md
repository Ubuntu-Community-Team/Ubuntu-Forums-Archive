---
title: "Problem with rapidly growing logs"
date: 2009-03-12
forum: General Help
---

### Post by thelawoffives on 2009-03-12
Three of my logs (messages, syslog and kern.log) are rapidly growing out of control, reaching 1.2-1.6 GB in a 24 hour span. I grepped the logs with the regex: '(fail|denied|segfault|segmentation|reject|oops|warn)' and the result was in the neighborhood of 15-70 lines for each log. The files I output from grep were all between 30-80 KB. The entries were all pretty benign, mostly related to minor graphics issues and maybe 8 or 10 segfaults.

I manually scanned the logs, but I was overwhelmed at the sheer number of entries, and the variety of kinds of entries, so I would not even know where to start. What puzzles me the most, probably, is that this is on a machine with a 7 day old install of Intrepid. I noticed this problem before I had installed any extra packages, so this is from the basic install. And, this was not a one time thing. I noticed it because the logs grew big enough to completely fill the disk over the course of 5 days. I deleted the logs and after a restart, the logs grew to 100 MB within an hour.

I guess I have three questions:

1) Does anybody have an inkling as to why this might be happening, or a way to determine why?

2) Obviously, there is a problem, but if there are not a ton of serious errors being reported in the logs, can I just bury my head in the sand and just write a script to get rid of the huge logs and run it with cron?

3) If I do set up a cron job, I would think that I would use the above regex, pull out the errors, save them to a file and remove the mega-log. Does any body see a real problem with that kind of set up? Is there a good log management package? I have never really had to do any serious log management, so I don't even know where to start.

Thanks for any help
Bill Henderson

---

### Post by thelawoffives on 2009-03-20
Over the course of a few days, I watched the logs looking for floods of entries and finally I saw a few hundred of these pop up: 

```
ACPI: EC: non-query interrupt received, switching to interrupt mode
```

I searched the last enormous log that I had saved and, indeed, there were thousands of these entries.

After some searching, I found [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284263]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284263"). I installed a 2.6.28.8 kernel and I am waiting to see if the problem repeats itself.

---

