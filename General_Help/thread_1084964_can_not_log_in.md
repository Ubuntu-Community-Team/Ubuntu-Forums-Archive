---
title: "can not log in"
date: 2009-03-02
forum: General Help
---

### Post by WmShkspr on 2009-03-02
Hi there. I am somewhat new to ubuntu, although not particularly new to Linux.  I have had a server running for a few weeks and when I tried to log in today, I could not do so.

When I log in at the console with a correct password, it just bumps right back to the username prompt. It does not say "access denied", as you would expect and as I get when I log in with an invalid username.

In addition, I am seeing this in the logs:
CRON[####]: pam_unix (cron:session): session opened for user root.

It is there about every 5 minutes. Thing is, I had only one cron job running and it was weekly. I disabled it and still get that message.

Could this be anything other than a hack?

---

### Post by wirelessmonkey on 2009-03-02
Could it be? Yes, but not likely.

Cron runs every 5 minutes by default, and more often if there are jobs scheduled more frequently. It runs and checks the crontab to see if there are any pending jobs.

My logs show the same, if you need more confirmation.

---

### Post by bodhi.zazen on 2009-03-02
I am going to re-title your thread to "can not log in" and move it to general help as you seem to be having a problem and you do not know what it is. You are guessing you have been hacked when there could be any number of reasons you cannot log in ;)

---

### Post by WmShkspr on 2009-03-02
More research is starting to look like I have not, in fact, been hacked. The fix to this bug seems to have gotten things running again, at least for now.

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/292791](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/292791).

That said, I didn't change the pam.d files originally, so I can't imagine what caused it in the first place. Strange bug, but at least it looks like I wasn't hacked!

---

