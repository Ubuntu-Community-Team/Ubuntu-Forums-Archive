---
title: "[SOLVED] adept and kdesudo crashes"
date: 2009-01-02
forum: General Help
---

### Post by Maerwyn on 2009-01-02
Hello, I have done several searches of the forums and have yet to find a post about either of these issues, which I think might be related. Your help is greatly appreciated.

I am using Kubuntu hardy 8.04

My husband and I are having the same trouble, which started at the same time. Both of us have internet connectivity, so this does not seem to be part of the issue.

Adept installer is not installing programs, it does not download the headers. It gets stuck at 0%,  and I eventually give up on it. 

I am having a similar issue with Adept updater. The headers freeze, and eventually the program crashes. The error says: "The application Adept Updater (adept_updater) crashed and caused the signal 11 (SIGSEGV)". 

It may be helpful to note that I have been able to install updates, and download applications in the past without any trouble, all this is a new thing.

Additionally, which may or may not be related:

Sometimes, after restarting we get this sudo error:

No command arguments supplied!
Usage: kdesudo [-u <runas>] <command>
KdeSudo will now exit...

Restarting does not seem to help. Please help!

---

### Post by Maerwyn on 2009-01-02
I just tried typing "apt-get update" in the terminal. but it froze, too.

---

### Post by Maerwyn on 2009-01-02
I don't know why but the issue seems to have solved itself. I kept trying to update/install software, and eventually it worked. I have no idea if the problem is going to reoccur, but I wanted to let people know that, for now, things seem too be working correctly.

---

### Post by geofurtado on 2010-07-05
I had this problem recently after installing Ubuntu 10.04 with an existing "home" directory.  It showed up after installing MoBlock (never ran into "kdesudo" before....

I renamed the ".kde" directory under my profile, then ran a test with "kdesudo nautilus" and the problem is gone.

Apparently, the first time kdesudo is run it, it needs to create the ".kde" directory and there was one already there from the pre-existing profile.

---

