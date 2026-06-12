---
title: "Gkrellm runs but invisible for 3 - 4 minutes"
date: 2006-07-09
forum: Desktop Environments
---

### Post by jonrkc on 2006-07-09
I've been using gkrellm to monitor system temperature and other items for three years.  Yesterday for no apparent reason it looked as though gkrellm was not running.  Ps ax showed that it was.  I reinstalled it and got the same result.  Then I noticed that three to four minutes after it loaded, it showed up on the desktop.  

Any ideas how to fix this?  I looked at syslog and can see nothing there that appeared related to this issue.  If there's something I can post that might help solve the problem, let me know and I'll do my best.

---

### Post by ShiningHolden on 2006-07-09
Is gkrellm on your session startup?

If so:
Try running the command to start it in a terminal.
See if you get any problematic output other than the app itself.
If you do, that is proubaly the problem? Try fixing the problem the output it outputing.
Also, make sure it is not due to another program on startup giving output, and gkrellm is behind that program, delaying it.

If not:
I have no idea.

---

### Post by jonrkc on 2006-07-09
> **ShiningHolden said:**
> Is gkrellm on your session startup?

If so:
Try running the command to start it in a terminal.
See if you get any problematic output other than the app itself.
If you do, that is proubaly the problem? Try fixing the problem the output it outputing.
Also, make sure it is not due to another program on startup giving output, and gkrellm is behind that program, delaying it.

If not:
I have no idea.
Thanks; I have no idea either.  I'd already tried your suggestions with no luck.  There was no error message anywhere that I could see, including in logs.  

Other things started going wrong after that, for example Thunderbird (my least favorite piece of software...that's another story) would show as running but not finish downloading messages, and eventually just disappeared, though its window-manager-supplied wire frame outline remained.  

Since I couldn't even use my email client, poor though it is, I decided to try restoring all my home directory files from a two-day old backup, after saving a couple of things I'd changed since then, separately.

To my surprise it worked.  Everything is so far working normally.  

I'll never know what went wrong; though I was getting lots of error messages about GCONF at various times--seemingly unconnected with Gkrellm, however.  I've been getting hundreds of GCONF error messages ever since I started using Linux (with Mandrake 8.0) three and a half years ago; so I generally just disregard them.  I've found I can even kill gconfd and it doesn't seem to make a bit of difference to things.

I get the impression sometimes that 70% of the running processes are probably unnecessary, but I lack the enthusiasm to spend 24 hours a day for several months finding out why so I can get rid of them.

Thanks again for your suggestions.

**Edit:** I reinstalled the home directory and it DIDN't fix the problem.  Then I really jumped into the fire and reinstalled everything ELSE from a two-day-old backup, sure it would not work and that I'd have to do a fresh install from the distro CD-ROM.  That was when I got the big surprise that everything was working again.  Makes more sense, too.

---

### Post by ardchoille42 on 2007-04-27
I'm having the same problem.. I launch gkrellm and it runs invisible for 3 minutes, then pops up on the desktop. There are no errors in the terminal. I am running Kubuntu Feisty.

Anyone got a fix for this?

---

### Post by dcstar on 2007-04-27
> **ardchoille42 said:**
> I'm having the same problem.. I launch gkrellm and it runs invisible for 3 minutes, then pops up on the desktop. There are no errors in the terminal. I am running Kubuntu Feisty.

Anyone got a fix for this?

Any issues with local hostname settings and DNS lookups?

---

### Post by ardchoille42 on 2007-04-28
> **dcstar said:**
> Any issues with local hostname settings and DNS lookups?

Now that you mention it, /etc/hosts has:

127.0.0.1       localhost
127.0.1.1       localhost

and I have no idea why the 127.0.1.1 entry is there. Would that have something to do with it?

---

### Post by ardchoille42 on 2007-04-28
Ok, new information about the "gkrellm running invisible for 3 to 4 minutes" problem - which I was also experiencing. I decided to tail /var/log/messages, run gkrellm and then tail /var/log/messages again and I got some info from /var/log/messages that hinted toward the firewall being misconfigured. So, I uninstalled the firewall and uninstalled KMyFirewall. Then I rebooted, ran gkrellm and it immediately popped up on the desktop.

Seems the "gkrellm running invisible for 3 to 4 minutes" problem on my machine was caused by a misconfigured firewall. Others who are experiencing the gkrellm problem may want to look into their firewall config.

---

