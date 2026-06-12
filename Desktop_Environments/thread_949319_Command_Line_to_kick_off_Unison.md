---
title: "Command Line to kick off Unison"
date: 2008-10-16
forum: Desktop Environments
---

### Post by Quarkrad on 2008-10-16
Can anybody point me in the right direction to work out what the command line is that I put into Scheduled Tasks in order to kick off some folder sync'ing via Unison?  I have set up some profiles in Unison to carry some local and they work if I go into Unison and manual Run them.  I understand I can do this automatically through Scheduled Tasks.  It looks straight forward to set up a Schedule but when it comes to the command line it appears to me you either know it or how to work it out.  For a newbi I feel lost in a black hole not knowing where to go.  Appreciate any starter for 10.

---

### Post by rwigle on 2009-01-21
I am trying to sort something very similar out as well.

I have a working profile that works fine from the command line with 

```
unison -batch
```

I use gnome-schedule, and have two events set up:

1. (command line above) at reboot
2. (command line above) every hour

If I use "execute task" in gnome-schedule, they work fine, but they don't seem to work otherwise. (???)

My default profile includes a root via ssh, and this seems to be the problem. I have rsa authentication working fine, and Unison is installed on both machines (Ubuntu Hardy 8.04)

Thanks in advance for suggestions.

---

### Post by dm_research on 2010-02-11
The following link might be helpful, at least in relation to running unison from the command line:

[http://www.stanford.edu/~pgbovine/unison_guide.htm](http://www.stanford.edu/~pgbovine/unison_guide.htm)

It also has some advice about how to run unison with a scheduler.

---

