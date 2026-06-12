---
title: "Questions about cron tasks"
date: 2009-02-01
forum: General Help
---

### Post by Shadowfaux on 2009-02-01
I've searched the net (read: google, ask and yahoo) and here to see if anyone has asked this before and no luck so i'll just ask away then.

I want to set up a cron task but i'm not 100% sure that it would work the way i want it to. I want it to visit a webpage and download a file from it, then either unzip the file to the directory or let me know that the file is downloaded. Is this at all possible or am i aiming to high with cron?

---

### Post by strider1551 on 2009-02-02
> I want it to visit a webpage and download a file from it, then either unzip the file to the directory or let me know that the file is downloaded. Is this at all possible or am i aiming to high with cron?

This is definitely possible.  Just make a bash script (or python script, or insert-language-here script) and have cron run it.

---

