---
title: "Cron &amp; Java: ELFCLASS32 error"
date: 2011-07-30
forum: Desktop Environments
---

### Post by cavemaneca on 2011-07-30
Well, I'll try to make this question as simple as possible.

I have cron set to run a script that calls a .jar every hour.
Running the script manually, via terminal or just opening it works without any issues.
Every time cron calls the script, the .jar fails to run with the ELFCLASS32 error.


So, google search results say a lot about 'forcing' 64-bit libraries, but that doesn't effect this.

To put it in my not-so-understanding way of thought...
WHY won't cron run the script the same way the shell does, and, if possible, how can I tell cron to run something the SAME WAY it's run as if I executed it myself?


I don't have a lot of experience with how cron runs, but obviously it doesn't work 100% the same as running something in terminal, or there wouldn't be issues like this. (And maybe there's a good reason for this, but I sure don't know it.)

---

