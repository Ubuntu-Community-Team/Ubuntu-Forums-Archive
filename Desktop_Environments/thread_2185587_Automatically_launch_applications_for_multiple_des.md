---
title: "Automatically launch applications for multiple desktop user accounts on startup"
date: 2013-11-03
forum: Desktop Environments
---

### Post by derekcentrico on 2013-11-03
We're ditching Windows entirely in our house.  I'd like to use my Ubuntu 12.04 home server in our transition.

That being said, I want it to automatically launch some apps for each user account when the server starts/reboots.

I'd like Google Music Manager, Remote Desktop, and other apps to automatically be up and running.

Granted, I know that I can setup startup applications.  However, those only seem to work for one user and do not seem to launch the apps for the other users until they sign on to their username.

Any thoughts out there?

---

### Post by ian-weisser on 2013-11-03
Why do you want client applications running for users that are not logged in?
Seems like quite a waste of power....

---

### Post by derekcentrico on 2013-11-03
I appreciate that and really don't want to debate the matter UNLESS there's a different solution.  My wife loves Chromebook and so we're ditching her old laptop.  Google, for whatever reason, doesn't support Google Music Manager on its own OS.  Also, there are some apps she needs and so I have a VM setup (Windows) for her to access on my Ubuntu home server.  The issue there is that Google prohibits VMs from running Music Manager.  

At this point, I'd like for her to be able to get her music files onto her Play cloud easily.  Having it setup with a shared folder and Google Music Manager running on Ubuntu would solve that.

The issue with two concurrent users at startup is because I actually use the home server with VNC as a computer and my user logs in automatically.  I cannot have two Music Managers running at once within my username from what I see because the .config files cannot be duplicated with different Google Accounts.

Any solution would be wonderful.

---

### Post by derekcentrico on 2013-11-03
Actually, I found an article since I last researched this Music Manager issue a year ago.  A different MAC ADDRESS for the NAT on the VM did the trick.  Wow.

So, now to ponder IF I even want this session crap since a Windows or Ubuntu VM will resolve issues.

---

### Post by ian-weisser on 2013-11-03
Glad to see you found a workable answer!

---

