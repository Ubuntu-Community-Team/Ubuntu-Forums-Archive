---
title: "[Urgent]Cant Boot Into Windows Only Ubuntu [Urgent]"
date: 2010-10-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by imsocruel on 2010-10-23
well i have made a mistake...
ok heres the story,
on windows i set so i dont have to wait a couple of seconds to boot into ubuntu but not i cant get into windows, 

can anyone help me with this?
this is urgent because i need windows for a couple of papers that are already saved on there

thanks

---

### Post by gibbylinks on 2010-10-23
Can you access GRUB. Hold down shift key after BIOS screen, then see if you can select windoze

---

### Post by sikander3786 on 2010-10-23
Easiest way, install StartUp Manager.

```
sudo apt-get install startupmanager
```

Access it from System > Administration > StartUp Manager and adjust the Grub timeout.

More info here.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

