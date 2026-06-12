---
title: "Load GNOME while filling in login credentials..."
date: 2008-11-27
forum: Desktop Environments
---

### Post by icanfly0307 on 2008-11-27
Hi there,
         I noticed that when the login screen comes up in Ubuntu, my hard drive shows no activity. So I was wondering, is it possible to have Ubuntu load GNOME while I'm filling in my login credentials? Windows does that and it's pretty handy 'cause it reduces the login time.

Any help would be appreciated. :)

---

### Post by Tamlynmac on 2008-11-27
Is login time really that critical. I guess it could be for some users. You might wish to read this:
[https://blueprints.launchpad.net/ubuntu/+spec/better-login-speed](https://blueprints.launchpad.net/ubuntu/+spec/better-login-speed)

Or maybe enable "Automatic Login".

---

### Post by icanfly0307 on 2008-11-27
Thanks for your link but it didn't really solve my problem. I distinctly remember reading about preloading GNOME but I can't remember where. Automatic Login really isn't an option since security is a big issue and it really doesn't increase the login speed. Any other thoughts? :)

---

### Post by Tamlynmac on 2008-11-27
I too recall reading something about "Upstart" (which I believe is a replacement for "SysV init") - just don't recall where. I do know that the adaptive readahead daemon "Preload" available in the package manager will not speedup your login.

Odd, my login speed increased when I enabled "Auto Login" - however, I was also concerned about security and disabled it.

Hopefully, someone else can add more insight.

---

