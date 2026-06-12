---
title: "Unity - Wireshark as root in launcher?"
date: 2011-06-15
forum: Desktop Environments
---

### Post by khaan on 2011-06-15
Hi,


Is there a way to have a shortcut icon in the Unity launcher to execute wireshark as root (gksudo wireshark) as opposed to simply wireshark with the current user permissions?


Thanks all!

---

### Post by mickyg on 2011-09-02
Just had to figure this out myself and thought I'd reply in case you still want to do this. The application shortcuts/launchers (whatever you want to call them) are stored in /usr/share/applications.

In that directory there is a file called "Wireshark.desktop", you need to open this as root and change the line near the bottom that reads ```
Exec=wireshark
``` to ```
Exec=gksudo wireshark
```

Save it and you're done!

P.S. I found while playing around with this that sometimes it worked straight away, other times I had log out and back in again for it to work.

---

