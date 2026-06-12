---
title: "Adept frozen. Can someone help?"
date: 2008-09-01
forum: Desktop Environments
---

### Post by Kaz Black on 2008-09-01
Hey all. I just recently installed Hardy Heron, and the KDE 4 desktop environment, and I'm having issues with Adept. While trying to download the sun java 6 package, Adept seems to have froze. I let it sit for close to 2 hours without any change, so I then switched off my computer, and attempted to run adept again, but every time I try, I keep getting the error message that its already running/another instance is already running, and I can't seem to unfreeze it. I was thinking about installing Synaptic from source, then uninstall Adept, but since its frozen, I can't get changeinstall and the one build program for converting source files into DEB. files. Can someone either help me unfreeze it, or get Synaptic running?

Thanks in advance

(PS. I have a 64 bit system.)

---

### Post by sonofusion82 on 2008-09-01
in terminal, try:

sudo apt-get update

then try to start adept again

---

### Post by Kaz Black on 2008-09-02
[B]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]
This is the message I get in terminal when I did that.

---

