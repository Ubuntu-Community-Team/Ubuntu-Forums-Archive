---
title: "Change username/admin? (from command line)"
date: 2006-01-23
forum: Desktop Environments
---

### Post by dudinatrix on 2006-01-23
Is there a way to change a username, and have all related records of the username be updated as well?  For example, say I want to change "david" to "dave", how can I do it to maintain everything such as the link of "dave" to any groups "david" was a part of, file ownership, etc.?

Also, in /etc/sudoers there's an %admin account... how can you switch that %admin account to another user?

---

### Post by cwaldbieser on 2006-01-23
[QUOTE=dudinatrix]Is there a way to change a username, and have all related records of the username be updated as well?  For example, say I want to change "david" to "dave", how can I do it to maintain everything such as the link of "dave" to any groups "david" was a part of, file ownership, etc.?
[/QUOTE]
As far as this first part goes-- try using "usermod".  You probably want to use the "-l" option and maybe the "-d" and "-m" options, too (see "man usermod").  Basically, all your security settings are by user ID (a number) rather than by name, so changing the name is no big deal.  You may or may not care about adjusting the home directory name.

---

### Post by dudinatrix on 2006-01-23
[quote=cwaldbieser]As far as this first part goes-- try using "usermod". You probably want to use the "-l" option and maybe the "-d" and "-m" options, too (see "man usermod"). Basically, all your security settings are by user ID (a number) rather than by name, so changing the name is no big deal. You may or may not care about adjusting the home directory name.[/quote]Thanks! I can't figure out how to use usermod (I'm feeling really dumb right now!) I assume it should be like...

"sudo usermod currentname -l newname"

but then I get "usermod: user newname does not exist".  Isn't it supposed to *change* it to "newname"??

---

### Post by dudinatrix on 2006-01-23
BAH!  Nevermind :)  I had it switched around.  Correct usage is:

sudo usermod -l newname currentname

---

