---
title: "local folders lost in thunderbird upgrade"
date: 2006-11-21
forum: Desktop Environments
---

### Post by rustybutt on 2006-11-21
I've been an 'IX user since '89 and became a Linux convert in '99.  I'm now standardized on Ubuntu Linux, Dapper Drake.

The problem I have is that I've been using Thunderbird since a bit before version 1.0 and I seem to be losing mail stored in the Local Folders.  Before that I used Mozilla for both web browsing and reading mail.  Poking around in the dot directories I see

~/.thunderbird/y6qve81l.default/Mail/Local Folders
~/.thunderbird/ihyjaqv8.default/Mail/Local Folders
~/.thunderbird.old/default/s3crnhww.slt/Mail/Local Folders
~/.mozilla/russ2/vzzhvqto.slt/Mail/Local Folders
~/.mozilla/russ/teew75op.slt/Mail/Local Folders
~/.mozilla-thunderbird/y6qve81l.default/Mail/Local Folders


Let me guess...   When I move to a new version of Thunderbird, it creates a new default directory and copies over some of the config information, but not my Local Folders, right?


So how the hell do I consolidate all of the Local Folders together so I have access to all my stuff again

Russ

---

### Post by marianom on 2006-11-21
Try this:
 create a few new dummies accounts (one for every "lost folder" you have) and  when they're created, access their "properties"->"server configuration"->"local directory". There, select for each account one of your old directories. This way you'll have your old mails in these accounts.
After it, select and move all of them to your real account, compress and erase the dummy accounts.

---

### Post by rustybutt on 2006-11-22
Hmpfff...  Good call.  Hadn't thought of that one.  I'll give it a go and will let you know.

Coolness

---

