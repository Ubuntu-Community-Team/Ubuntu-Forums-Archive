---
title: "Force Evolution to archive mail spool?"
date: 2007-05-31
forum: Desktop Environments
---

### Post by scarolan on 2007-05-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/27014](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/27014) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Greetings all - I'm using Evolution for my email on Ubuntu Feisty.  I have it set up to read the mbox mail spool /var/mail/scarolan as my inbox.  

When I move read messages to an archive folder they don't really get moved, instead it appears Evolution just leaves them in the inbox and creates some sort of virtual folder.  I verified this by running mutt and found there were thousands of messages in the file.

The more mail piles into the inbox, the longer it takes Evolution to start up and scan the inbox folder.  It's getting to the point where I get errors nearly every time it starts up.

Is there any way to force Evolution to purge the mail spool and actually MOVE messages into subfolders?  The "Summary and folder mismatch" error I get is summarized in the bug report below.  I believe this is at least partly caused by the gigantic mail spool which Evo seems to choke on every time I start it up.

---

### Post by scarolan on 2007-05-31
I think I have fixed the problem - I backed up the mail spool and created a new one and it seems to have cleared out all the extra messages.

---

### Post by andrew.46 on 2007-07-05
Hi,

 Read your post with great interest, partly quoted below:

> **scarolan said:**
> [
When I move read messages to an archive folder they don't really get moved, instead it appears Evolution just leaves them in the inbox and creates some sort of virtual folder.  I verified this by running mutt and found there were thousands of messages in the file.
.

 I am sure you have good reason but why not stick with mutt?

                       Andrew

---

### Post by scarolan on 2007-07-05
I needed an integrated calendar so I could accept email invitations from management.  Since then, however I've switched jobs and am back on MS windows on my desktop.

---

