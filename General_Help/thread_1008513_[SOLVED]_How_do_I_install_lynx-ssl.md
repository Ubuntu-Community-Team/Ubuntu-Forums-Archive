---
title: "[SOLVED] How do I install lynx-ssl?"
date: 2008-12-11
forum: General Help
---

### Post by luomat on 2008-12-11
I searched the forums and saw someone suggest to just install 'lynx-ssl' but that was ~2 years ago and no longer seems to work.

I tried this:

ubuntu% sudo apt-get install  lynx-ssl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**Note, selecting lynx instead of lynx-ssl**
lynx is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

The bold line above indicated there was a problem, I searched around and didn't find a lynx-ssl package anywhere and Google didn't help either.

I thought I'd try it to see if it "just worked" but was told

"Alert!: This client does not contain support for HTTPS URLs."

so I'm clearly missing something.

This is on 8.10.

Thanks!

---

### Post by Sorivenul on 2008-12-12
There is a [bug]("https://bugs.launchpad.net/ubuntu/+source/lynx/+bug/290926") related to this in Launchpad.  The solution seems to be installing "lynx-cur", as it has replaced "lynx-ssl".

---

### Post by luomat on 2008-12-12
> **Sorivenul said:**
> There is a [bug]("https://bugs.launchpad.net/ubuntu/+source/lynx/+bug/290926") related to this in Launchpad.  The solution seems to be installing "lynx-cur", as it has replaced "lynx-ssl".

Thanks, that worked.  There was a warning about the old lynx configuration file, but otherwise it seems to have worked fine.

---

### Post by Sorivenul on 2008-12-12
If your issue is resolved, please mark this thread "SOLVED" using the Thread Tools link at the top of the page.  

Good luck!

---

