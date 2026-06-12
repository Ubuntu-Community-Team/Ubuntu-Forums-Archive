---
title: "Schedule a script to set the time~!"
date: 2006-05-04
forum: Desktop Environments
---

### Post by lucas.clemente on 2006-05-04
I have a vmware install of ubuntu. For some reason, the clock is SLOOW. for every 2 minutes that go buy, my clock loses one. (I.e I set my lock at 9:00, and now at 9:10, my ubuntu box says 9:05.)

I wrote a quick sript to set the time: 
net time set -S servername.com

good stuff. But I want to schedule it to run as root every five minutes. How do I do that?

---

### Post by mmcmonster on 2006-05-04
It sounds like you want to create a cron job.  I'm not sure (I'm not on my Ubuntu machine at the moment), but I think you should be able to set a cron to run every five minutes.  (I'm sure you can set for hourly or daily).

Sorry I'm not much more help. :-(

---

### Post by cgjones on 2006-05-04
First, run this command in the terminal.
```

crontab -u root -e

```

You should now be in the crontab editor. Add this line.
```

*/5 * * * * net time set -S *servername*

```

Save, and that should be it. On a side note, depending on who servername.com is, you might want to be using a command like rdate or ntpd. Also, if this is a public server, updating every 5 minutes is a little excessive.

---

### Post by lucas.clemente on 2006-05-04
Perfect!! That appears to have done it~!

It's not a public server, it's one we have here at work. 

out of curiosity, what's the */5 * * * * for?

---

### Post by cgjones on 2006-05-04
Glad to hear that it worked. I got a little nervous at first, because I didn't want you hammering some poor sysadmin's ntp or smb server. The */5 basically tells it to run every 5 minutes. It is kind of tricky to explain, so here is a link that sums it up quite nicely.
[http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)

---

### Post by louis_nichols on 2006-05-04
Vmware machines have internet access, so you might try to set your clock to sync with a ntp server.

---

