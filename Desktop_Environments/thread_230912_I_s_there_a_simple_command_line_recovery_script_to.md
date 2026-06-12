---
title: "I s there a simple command line recovery script to get back default settings?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by kurty on 2006-08-06
I screwed somthing up by trying to change resolution while updating the system, now I get the login screen but after logging in  I get no desktop, no response from the keyboard, only a mouse pointer. I don't have a backup (I know..), and I am afraid to lose some data from a re-install. Is there away to get things back from recovery mode. PLEASE NOTE I AM A LINUX AND COMMAND LINE NEWBY.

thanks

Kurty

---

### Post by roozbeh.daneshvar on 2008-02-12
At least you can try this to change configuration:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

