---
title: "Random freezing (this time, I have error logs)"
date: 2009-03-02
forum: General Help
---

### Post by AndrewTheArt on 2009-03-02
Hey everyone --

This is what my laptop is running -- 

```
Linux andrew 2.6.27-12-server SMP i686 GNU/Linux
Ubuntu 8.10
```The hardware specs, if needed are here --

[http://pastebin.com/m7e66ff7c](http://pastebin.com/m7e66ff7c)

My laptop has been randomly freezing once every two or three days now (it generally happens after waking up from sleep/standby, but it can happen at any time after that too. If it does happen after a resume from sleep, it happens fairly soon after). The only way to shock it back to life is to hard-reset the entire machine.

However, this time I got smart and wrote down the time it froze up for later debugging purposes (it was at 07:04:41, approximately) 

I was wondering if anybody could spot anything I didn't.

Here's the result of a

```
cd /var/log; grep "07"04" *
```(so the following link should have most/all log entires on my machine in the minute 07:04)

[http://pastebin.com/m5b00b1de](http://pastebin.com/m5b00b1de)

Here's messages from /var/log/syslog, /var/log/messages, /var/log/kern.log, and /var/log/daemon.log from the minute I woke up my laptop from it's sleep this morning to to the minute I had to hard restart it (so right before the freeze). Looks like all entires are within the 7:04 range, meaning my laptop froze not long after I woke it up...

[http://pastebin.com/m6d3890a](http://pastebin.com/m6d3890a)

What's interesting is that I'm not seeing anything particularly interesting in the logfiles "right before" the freeze -- I'd expect to see *some* clues, but seemingly there is not indication that the entire machine is about to freeze up.

If anyone could provide any help, that would be greatly appreciated. This error is bad enough that I will no longer be able to use Ubuntu if I don't resolve it (I'm just losing too much work - maybe I could reinstall Ubuntu, but that's a pain in the butt). I'm pretty persistent though, so I'm going to look around so more in the logs to see if I missed a line. But multiple eyes are > one (;

---

### Post by AndrewTheArt on 2009-03-02
Bump

---

