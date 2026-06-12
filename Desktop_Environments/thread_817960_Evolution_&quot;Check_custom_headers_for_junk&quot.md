---
title: "Evolution &quot;Check custom headers for junk&quot; not working"
date: 2008-06-04
forum: Desktop Environments
---

### Post by chmac on 2008-06-04
My server run spamassassin on incoming mail. Evolution has an option under Edit > Preferences > Mail Preferences > Junk called "Check custom headers for junk". The default options are:
X-Spam-Flag = YES
X-Spam-Level = ****

I've selected the option. I've selected "Check incoming messages for junk".

When a mail arrives with those two header set, it doesn't get put into the junk folder. It appears as normal in my regular folder. Anyone know how I can change this?

I had it set as a filter, but processing filters can be quite slow when I download a lot of mail (over IMAP).

Any suggestions would be appreciated.

---

### Post by qrwe on 2010-05-18
Hello,

I've had exactly the same problem. I'm usually a Thunderbird user, but wanted to give Evolution a chance. I like it a lot, except this very annoying bug/feature.
I've tried to create a custom message filter, for which it checks for weather the specific header "X-Spam-Level" contains "***". If so, it marks the mail as junk at puts it in the Junk folder. Unfortunately, this didn't work either.
How have you guys succeeded with your spam checks (except "I use Gmail", etc)?

---

### Post by qrwe on 2010-05-18
OK, to help others who may have this problem, I finally found a how to do this. Surprisingly enough, it wasn't a bug at all: you have to explicitly enable message filtering in another separate check box!
[LIST=1]
[*]Hit Shift+Ctrl+S for preferences
[*]Mark the mail account you wish to enable message filtering for under "Mail Accounts" and click "Edit"
[*]Choose the "Receiving Options" tab
[*]Check the box "Apply filters to new messages in INBOX on this server"
[*]Check the box "Check new messages for Junk contents"
[*]Done. Enjoy a less spam tainted world!
[/LIST]
It's remarkable that these boxes aren't checked by default! It would have spared many confused minds..

---

### Post by qrwe on 2010-05-18
..and by the way, chmac doesn't seem to be very active in this thread anymore. If you (chmac) see this, or if you're an admin: please mark this thread as SOLVED!

---

### Post by chmac on 2010-06-15
Steady on, steady on. 3 messages in a row some 23 months after my original question, and within a few days I'm no longer active. I don't know about that... :-)

I've since moved onto a new mail server which automatically puts my mail into different folders. Personally, I'm pretty sure I'd tried checking all of those boxes when I had this issue. Nowadays I'd file it as a bug, but back then I wasn't so familiar with bug tracking. I'm assuming it was a bug and it's sinced been fixed.

Anyway, I'll mark the the thread as solved. Maybe it'll help somebody else with the same issue.

---

