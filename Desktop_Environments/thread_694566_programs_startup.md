---
title: "programs startup"
date: 2008-02-12
forum: Desktop Environments
---

### Post by kaiwan on 2008-02-12
Hi!

 I have gutsy - gnome.

My problem is that skype, kmess, VirtualBox and Kmess open when I log in.

They are not set to start (under Sessinons) when starting ubuntu and
option for remembering running application when logging out is disabled.  

Any ideas?

---

### Post by mali2297 on 2008-02-12
Remove the file **~/.gnome2/session**. (Enable *view hidden files* if you use Nautilus.)

Also, see if there are any files in the directory **~/.config/autostart/**.

---

### Post by kaiwan on 2008-02-12
done it ... its ok now ... thanks

---

