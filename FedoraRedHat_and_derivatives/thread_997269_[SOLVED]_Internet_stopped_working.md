---
title: "[SOLVED] Internet stopped working"
date: 2008-11-29
forum: Fedora/RedHat and derivatives
---

### Post by COLiNx86 on 2008-11-29
I recently installed fedora 10 but last night my internet stopped working(this is all on a laptop). I installed kde 4.1.3 last night and started it (way to slow), so I went back to gnome and typed into a terminal sudo yum groupremove "kde (k desktop environment)" .After it finished some error about the network manager showed up. But the internet kept on working, I turned off my computer and went to bed. When I woke up and turned on my laptop the internet wouldn't work, whenever I plug in the ethernet cable it doesn't do anything either. And no matter what I do I can't get it to connect. any idea?

---

### Post by YeOK on 2008-11-30
> **COLiNx86 said:**
> I recently installed fedora 10 but last night my internet stopped working(this is all on a laptop). I installed kde 4.1.3 last night and started it (way to slow), so I went back to gnome and typed into a terminal sudo yum groupremove "kde (k desktop environment)" .After it finished some error about the network manager showed up. But the internet kept on working, I turned off my computer and went to bed. When I woke up and turned on my laptop the internet wouldn't work, whenever I plug in the ethernet cable it doesn't do anything either. And no matter what I do I can't get it to connect. any idea?

hmm.. 

Make sure the 'NetworkManager' deamon is running, type 

```
 $ su -c "service NetworkManager start" 
```

It could be that KDE messed with your GNOME sessions, so goto 

'System > Preferences > Personal > Sessions'

Make sure 'Network Manager' is clicked.

---

