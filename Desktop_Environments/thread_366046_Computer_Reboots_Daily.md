---
title: "Computer Reboots Daily"
date: 2007-02-20
forum: Desktop Environments
---

### Post by SuperMike on 2007-02-20
My Dapper version of Ubuntu is restarting daily. Is this likely a kernel bug from a new kernel? I mean, is this a known issue going around? No other clues seem to be told in the event log. It just restarts. The last restart was 8:20am this morning before I arrived.

I was doing fine for quite awhile until this.

---

### Post by Jeremy23 on 2007-02-21
Restart, as in cleanly starts shutting down then comes back up again? Or just goes -blip- off and -blip- on?

---

### Post by SuperMike on 2007-02-21
I can't determine it yet. It's consistently at approximately 7:40 or 22:00, but may be delayed an hour here or there. I'm also working with the power company to see if it's a problem there, and so far they say they are having issues too. My well keeps going out on a daily basis because of the power issues and I have to reset it.

Does the syslogd restart every day? The way I've been detecting these restarts is:

# cat /var/log/messages | grep -i restart

and I get a report back about syslogd restart. I noticed when I restart a PC it puts an entry of syslogd restart there.

However, at my office, I have the whole building on a generator, and my distro is Dapper there, and when I grep the restarts I see:

# cat /var/log/messages | grep -i restart
Feb 20 08:22:55 txcsflnxw1 syslogd 1.4.1#17ubuntu7: restart.
Feb 20 12:53:03 txcsflnxw1 syslogd 1.4.1#17ubuntu7: restart.
Feb 21 07:38:15 txcsflnxw1 syslogd 1.4.1#17ubuntu7: restart.

...which shows a 7:38am restart when I never did that. The 12:53 restart was an accident -- pushed the wrong power button on a box. The 8:22am one was one I never did because I wasn't in the office that soon.

---

