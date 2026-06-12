---
title: "DesktopEnvironmentsandAutoRUN?"
date: 2012-10-16
forum: Desktop Environments
---

### Post by MoralAnarchy on 2012-10-16
Hey all,
I have both Unity and Kubuntu installed on my machine(using Ubuntu 12.04 btw) and I have a conky autostart file saved.  The thing is I only want conky to autostart when I open up my Unity desktop and not when I start Kubuntu.  Is there any way I can do this?

---

### Post by LewisTM on 2012-10-16
Open your autostart .desktop file inside a text editor and add this line:
```
OnlyShowIn=Unity;
```

Cheers!

---

### Post by MoralAnarchy on 2012-10-16
Thanks a lot my friend!  Have a nice day!

---

