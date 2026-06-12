---
title: "Pidgin: Buddy from Ubuntu always seen as offline"
date: 2009-06-24
forum: General Help
---

### Post by UranUtan on 2009-06-24
Hi,

Using Ubuntu 9.04 x32 and x64 + Pidgin, all systems up to date.

When I sign up with an MSN account, I can see all other MSN buddies when they are from a Windows machine. But if the MSN buddy is also using Pidgin under Ubuntu, then I always see it as offline.

The MSN - Pidgin - Ubuntu in question is in another computer same LAN at home, is it a problem? And BTW if the same user, instead of using Pidgin uses MirandaIM (under Windows) instead then I can see it online.

What is wrong?

Thanks in advance for any help.

---

### Post by UranUtan on 2009-11-07
Answer to self (and solution):

The issue still exists with Ubuntu 9.10 (using Xubuntu 9.10 x32 with the default Pidgin 2.62). When I signed in, some users see it as offline and some see it online. It seems to affect only MSN users created around 2008, 2009.

I've tried to log in using Miranda IM v0.89 (Windows) and the issue is the same. I cancelled the MSN account and recreated it. After that, the account works OK with Miranda IM Windows but not with Pidgin.

I installed Empathy 2.28.11 and the account now works OK. So conclusion, this is a Pidgin bug.

---

### Post by NFblaze on 2009-11-07
Perhaps you should file a bug report.

---

### Post by UranUtan on 2009-11-07
> **NFblaze said:**
> Perhaps you should file a bug report.

This bug has been files in launchpad.net, a long one and which has been closed due to difficulty to reproduce the bug (b/c it depends on some specific MSN accounts). I have lost the link (found it by Google). I have also read a similar long standing thread in this forum where there is no conclusive solution.

I would file a bug if there was some hope. But now Pidgin is being phased out and Empathy has fixed the issue. The Pidgin Team knows about this issue (it has to do with old MSN protocol).

---

