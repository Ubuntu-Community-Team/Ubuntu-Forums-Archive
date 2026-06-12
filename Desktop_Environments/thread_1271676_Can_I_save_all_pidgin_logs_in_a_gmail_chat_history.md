---
title: "Can I save all pidgin logs in a gmail chat history?"
date: 2009-09-21
forum: Desktop Environments
---

### Post by sampathonline on 2009-09-21
Hi,

I was using office jabber account via  pidgin. My system got crashed and I needed to format the hard disk and lost all my data. Now all my pidgin chat history is lost [although fortunately some logs I had backed up in home pc from .purple directory]

So the below questions arise from the problem?

1) Is there a way where I can store all the pidgin chat logs in a centralized server?
Does pidgin allows this atleast through any plugins?

2) Ideally, I would prefer all pidgin chats to be stored in gmail chat history. I have an idea regarding it, but not sure how to implement this. "No matter, from where you receive message, configure pidgin in a way so that it redirects to your gmail account, so that all your chats gets stored in gmail chat history.

So, is there a way out of this...

---

### Post by willlarson on 2009-09-23
I've managed to find a clunky workaround for this.  The Gmail IMAP server has a two-way feed, meaning that you can also upload mail messages.

My method was to write a script to navigate through the .purple log folders and generate an email for each log file.  Then each email is uploaded into Gmail through the IMAP interface.  Tip: create a filter in Gmail ("Pidgin Chats" for example) and upload directly into that virtual folder through IMAP.

Username:
There's sufficient information in the logs to deduce the username, from which I was able to programmaticly create an email address.  For Instant Messenger, a function checks to see if the username is an email address.  If not, it removes spaces then adds "@aim.com" to the end of it.  This can also be applied to your usernames if you communicate through various usernames/networks.

Archival frequency:
My script has to go into the IMAP interface to deduce when the last chat was archived before figuring out by which date range to filter the log files.  Tip: Make sure not to archive any logs that might still be active or you'll get half files and duplicates.  I cut off my date range filter at the end of the previous day.

I know this isn't a full solution for you but I hope it helps.  Unfortunately my code is very buggy and I've been rewriting parts of it.  It's definitely not ready for an Alpha release, but I'll post it when I feel it is.

---

### Post by sampathonline on 2009-09-25
Hi thanks for the reply.

Running script to mail the log files each time looks bit complex.

But again, the simple solution wud be:
"Keep both of yourr Jabber and Gmail accounts active in pidgin and 
just direct any incoming messages received by your Jabber account into Gmail Account" [Rest will take care of itself]. But the question is HOW?

---

### Post by storms on 2010-11-02
Did you have any luck progressing with this script? I am keen to try it, and perhaps adapt it to use with Kopete to. (I use gtalk but also other protocols, so the other solution suggested would not work for me).

Many thanks!

---

### Post by emilgenov on 2010-12-08
I've needed same functionality, that's why I've created project to help me import my pidgin history into gmail account. If anybody wants to try it, [it's hosted in google code]("http://code.google.com/p/im-history-converter/")

---

