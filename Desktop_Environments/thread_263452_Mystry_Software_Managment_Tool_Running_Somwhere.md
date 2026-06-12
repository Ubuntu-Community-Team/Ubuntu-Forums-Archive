---
title: "Mystry Software Managment Tool Running Somwhere?"
date: 2006-09-23
forum: Desktop Environments
---

### Post by moeFinley on 2006-09-23
My update notification icon has popped up but when I click on it I get a message stating there is already a software managment tool open.  I've got nothing else open and a quick browse through System Monitor doesn't seem to show any likely cadidates.

I'm new to Linux (about 4 months now), what should I be looking for?  Is this a bug with the notifier?

I've been looking for Synaptic, Adept.  The only thing running is update-notifier.  Is it safe to try killing this process and then loading synaptic?

apt-get gives me this message:```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

Any solution/pointers would be great! Thanks :D

---

### Post by moeFinley on 2006-09-23
Sorry, think I've just fixed it?  Something to do with a failed Flash plugin install?  All I had to do was run the installer again and when it asks me if I wanted to install Flash I just said no.

I don't understand what was happening though, maybe someone could enlighten me?

Why would this failed install keep apt-get running, even when I reset my machine? :confused:

---

