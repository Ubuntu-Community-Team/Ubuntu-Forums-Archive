---
title: "thunar doesnt follow default icon set"
date: 2011-10-17
forum: Desktop Environments
---

### Post by Tares on 2011-10-17
hello,

I've "installed" some icons into my .icons folder, selected it from the settings menu, rebooted and my icons changed. However thunar somehow doesn't want to follow those icons. Any idea how to change that? 

I've attached screenshot which shows the issue.

---

### Post by LarsKongo on 2011-10-17
You aren't running Thunar as an administrator are you? (Not recommended.)
Administrator accounts don't use icons installed in *.icons*. Admin accounts use icons installed in */usr/share/icons*.

---

### Post by Tares on 2011-10-17
No, I'm running it as a normal user. Well, .icons are working, because everywhere else they are showing correctly. Only thunar has some issues.

---

### Post by Tares on 2011-10-18
Okay, I've found the culprit. It seems that my icon set was a little bit old. I've changed it and now everything is working fine.

Although with old one, when I've changed icons manually (Settings Manager -> View -> Icons) everything was fine until reboot. Then the Thunar icons became like in the attached file.

Anyway, I'll mark this thread as semi-solved.

---

