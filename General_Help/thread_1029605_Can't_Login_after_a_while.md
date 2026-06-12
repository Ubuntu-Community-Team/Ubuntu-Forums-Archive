---
title: "Can't Login after a while"
date: 2009-01-03
forum: General Help
---

### Post by dnoyeb on 2009-01-03
At some point I notice that my server in the basement is not responding.  Usually this happens when I try to access a Samba share.  So I open up ssh and try to login to check it out.  But ssh just hangs there.  Then I go downstairs, ctrl-alt-F1 to the first console and try to login there.  I get a bunch of the normal text, but instead of loging me in, it stopps and hangs.  The graphical login does the same thing.  Just hangs.

So this is not a complete OS hang, it just won't allow any authentication to succeed and all methods hang.

I ctrl-alt-del, and the thing starts to shut down.  It takes a long time for a few of the processes to shutdown, but ultimately it reboots and everything is back to normal.

Anyone experience this before?

---

### Post by ibuclaw on 2009-01-03
Could you provide some information that could possibly suggest why this is happening? Such as the logs from the time of your attempted Samba connection to the point you shutdown/reboot the system?

That may provide the best evidence to find out what is happening.

Regards
Iain

---

### Post by dnoyeb on 2009-01-06
Its not just samba, its local login, ssh login, any type of login.  I have tried to find anything in the logs but I haven't see any errors.

And of course, when I can't log in, I can't see the logs.  But after reboot I can.

Any particular log I should look in?

---

### Post by dnoyeb on 2009-01-07
I'm going to try and disable my other 2 unused network cards and see if that makes a difference.  Last night it happened and I think the most recent thing in the log was some DHCP stuff.

---

### Post by dnoyeb on 2009-01-09
turning off the extra network cards in BIOS didn't help.  disabling ipv6 didn't help.

Now I have unloaded my HVR-1600 driver.  Ill see if that does anything though I can't imagine why it would affect login.

---

### Post by dnoyeb on 2009-01-13
The driver being unloaded does not seem to make a difference.  I'm not entirely sure.

But here is an interesting thing I found.  The shells already logged in, function as normal.  They are not locked up or anything.  But any new login fails.  So sudo fails as well.  And it fails with a lockup of that shell.  So I think there is something wrong with the shell.

I think the next thing to try is to log in as a different user when this happens.  Maybe there is something wrong with just my user login process or scripts.

Hmm, and I think this is why cron gets stuck because it cant login to execute the scripts.

---

### Post by dnoyeb on 2009-01-16
The reason nobody/no process can complete the login process has to do with either klogd or ksyslogd.  I wasn't paying enough attention to figure out which.

When I restarted one of those, the logins that were blocking completed.

Ill post a new topic to figure out why that is.

---

### Post by dnoyeb on 2009-01-22
Interesting that my server has now been up for 8 days.  Of course I too have been up with work for about 8 days, so maybe its because I have not been using it.  But I dont think so.  Every since I restarted those log daemons, the system has not locked up!

---

### Post by Yashiro on 2009-01-22
Problem writing to a log maybe. Have you ran *fsck* on the filesystem too?

---

### Post by dnoyeb on 2009-02-02
System started acting up again.  everything was going slow and I could not get any email.  I restarted klogd and everything is flowing again.

How can I tell what is blocking klogd from doing its thing!?

---

### Post by dnoyeb on 2009-02-06
It acted up again but restarting klogd did not fix it.  I had to restart sysklogd.

I did a fsck and no problems.

Anything I should look for?  Maybe just update to latest kernel and pray?

---

### Post by Yashiro on 2009-02-06
You could clean out the log folder manually then reboot.
Re-install klogd and sysklogd.
Re-install logrotate.
Install syslog-ng instead.

You're not running out disk space are you?

---

### Post by dnoyeb on 2009-02-25
Its an old bug.  Probably should be in release notes or something.

[https://bugs.launchpad.net/ubuntu/+source/sysklogd/+bug/26986](https://bugs.launchpad.net/ubuntu/+source/sysklogd/+bug/26986)

---

