---
title: "Session Logging Out On Its Own"
date: 2007-05-15
forum: Desktop Environments
---

### Post by _simon_ on 2007-05-15
My other half has a problem with her fresh Ubuntu 7.04 install.

Her Gnome session logs itself out on it's own when she's using firefox.

I've tried deleting .mozilla AND downloading FF from the mozilla site rather than using the one that comes with Ubuntu but it still does it.

Any ideas as to what's going on?

---

### Post by _simon_ on 2007-05-15
Ok it doesn't appear to be firefox related as it's just done it whilst she was using Opera.

---

### Post by Soybean on 2007-05-15
I saw in another thread recently that under some circumstances (I didn't really look into it to find out what the circumstances were), Ubuntu can end up configured such that shift-backspace kills X. This would look a lot like logging out of Gnome, and shift-backspace is a key combination that could easily come up during normal web use. 

So I'd say, go over to her computer (while it's logged on) and hit shift-backspace and see what happens. If it bumps you to the login screen, it's probably the culprit, and you'll just need to adjust some keybindings (or she'll need to studiously avoid pressing those two keys at the same time ;)).

If that isn't the problem, I would still guess that X dying is more likely than Gnome logging itself out. So that's another angle you could consider in your troubleshooting, at least.

---

### Post by _simon_ on 2007-05-15
Thanks for the suggestion, it's not shift + backspace though. Earlier it did it when she wasn't even touching the keyboard.

---

### Post by Soybean on 2007-05-15
Ah, too bad, that would've been a simple fix. Well, in that case, I'd start trying to find a log with an error message in it. Hopefully someone else has a suggestion... I've never been very good at knowing which log to look in, so I usually just go to /var/log/ and start opening things at random. ;)

---

### Post by _simon_ on 2007-05-15
Thanks, I'll take a look through the logs and see if here's anything that makes sense to me lol

---

### Post by _simon_ on 2007-05-15
Right, this appears in the /var/log/messages and in /var/log/syslog and /var/log/user.log

```

Received signal 15, shutting down cleanly

```

---

### Post by _simon_ on 2007-05-15
Update: Noticed that she had a lowlatency kernel installed for some reason. 

Have now removed that and using the generic... hopefully all will be ok now.

---

### Post by _simon_ on 2007-05-16
Well this seems to have resolved the issue! :D

---

### Post by seb_renaud on 2007-05-16
Hi, I seem to have the exact same problem with Dapper. I am not sure how to change the kernel to " Generic " or if in fact I have the generic. I would gess not from this:

```

$uname -a
Linux station345 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686 GNU/Linux

```

Can you point me in the right direction on how to change the kernel?

---

### Post by Soybean on 2007-05-17
I don't believe there is a generic kernel for Dapper. The 386 kernel that you've got there ought to be pretty stable. If simon's problem was actually being caused by the low-latency kernel, then you may have a different problem with similar symptoms.

Hmm. If the kernel IS the problem, though, I think there should be errors showing up in dmesg. Hopefully someone will correct me if I'm wrong there... like I mentioned above, I'm not great at identifying the correct log file. ;) Is there anything interesting towards the end of your dmesg?

---

