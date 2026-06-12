---
title: "gnome-session-autosave bug"
date: 2019-05-23
forum: Desktop Environments
---

### Post by szymon.antas on 2019-05-23
Guys could you please confirm whether there is still an existing bug for saving gnome session  since it has switched to gnome3?
I believe I've been following a recommended step requiring activating the below in dconf Editor:
/org/gnome/gnome-session/auto-save-session [ -> ON]
If the bug still exists does anybody know any good solution in a meantime?
I personally use few workspaces with multiple windows/apps and on top of that each of my windowa is specifically resized for the screen. When I log back on after restart I loose everything.

I don't want to come back to Windows OS, please.

Thanks a lot.
------------------
[SIZE=1]System:
  Host: szymon-X510UAR Kernel: 5.0.0-15-generic x86_64 bits: 64 
  Desktop: **Gnome 3.32.0** Distro: **Ubuntu 19.04** (Disco Dingo) 
Machine:
  Type: Laptop System: ASUSTeK product: X510UAR v: 1.0 
  serial: <root required> 
  Mobo: ASUSTeK model: X510UAR v: 1.0 serial: <root required> 
  UEFI: American Megatrends v: X510UAR.308 date: 03/13/2018[/SIZE]

---

### Post by logix2 on 2019-05-23
Yeah, that dconf setting has not worked in a long time. I use this instead to manually save and restore apps/windows and their positions: [https://www.linuxuprising.com/2018/04/gnome-save-and-restore-running.html]("https://www.linuxuprising.com/2018/04/gnome-save-and-restore-running.html")

---

### Post by szymon.antas on 2019-05-24
Hi @logix2 thanks for your response. i followed the steps described however I received plenty of errors while installing npm. i think im gonna just suspend my laptop - the easiest solution ever ; )

---

