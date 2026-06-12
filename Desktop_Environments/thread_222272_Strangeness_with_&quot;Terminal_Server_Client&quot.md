---
title: "Strangeness with &quot;Terminal Server Client&quot;"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Harrkev on 2006-07-24
OK.  This is strange.

I have an XP box with a few apps that I need to be able to use from time to time, so it supports terminal services (through a small hack).

I also have a fresh Dapper box.  I installed, upgraded, installed nVidia graphics drivers, and ran "Easy."  I made three user accounts: one for admin purposes, one for me, and one for the wife.

The funny thing is that my account can use the "Terminal Server Client."  I can remotely log into my XP system and run everything great.  My wife's account, on the other hand, dies.  When I run the program, as soon as I hit "connect," the window completely disappears.  The two processes, "tsclient" and "rdesktop" are still running (but show as sleeping).  I have checked, and the settings are the same for both.

So, why would two, otherwise identical Terminal Server Client apps behave differently.  My 1st guess would be a permission problem but both user accounts were created at the same time and in exactly the same way.

Any ideas?

---

### Post by cptnapalm on 2006-07-24
I'm not up on this, so my advice is only a test case usage.  I would try creating another user and then attempt it.  If it works, then there is *something* wrong specifically with your wife's setup.

One thing to check, perhaps, would be /etc/group.  Find all instances of your username and make sure that your wife's account too is in all the same spots (excepting the user specific group, of course.)

This might not be much help, but I thought I'd throw at least a couple of checks out there, just in case.

---

