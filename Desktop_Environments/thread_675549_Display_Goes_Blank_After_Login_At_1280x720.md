---
title: "Display Goes Blank After Login At 1280x720"
date: 2008-01-22
forum: Desktop Environments
---

### Post by zemon on 2008-01-22
I have an odd display problem. First the configuration:
IBM / Lenovo T60
Intel 945 integrated graphics
Ubunty Gutsy 7.10

Everything works fine in everyday use. I can use the internal monitor at 1280x800 resolution or an external (larger) monitor. Do note, though, that this laptop does not seem capable of switching between them without restarting X (Ctrl-Alt-Backspace) and it does not seem capable of running in dual-screen mode. I get one screen. If I restart X with the external monitor attached, the screen nicely displays on the external monitor and (as much as will fit) on the internal LCD.

But... things don't work so well when I hook up my Optoma projector as an external monitor. The projector has a resolution of 1280x720. I hook it up to the VGA port and restart X.

The login screen displays a little oddly. Everything is there but the bottom "menu bar" is moved up and there is some blank desktop showing beneath it. It looks like the useful part of the screen is formatted within a 1280x720 area even though X is running in 1280x800 mode. I *can* see this on both the internal LCD and on the external project. All is good (enough).

But after I log in, both internal and external displays go blank. Done. Kaput. I *suspect* that X is switching to 1280x720 resolution and the video can't do it but I don't know how to confirm that.

Is there any way to force the system to stay at 1280x800? Or maybe some other resolution?

Thanks,
-- Art Z.

---

### Post by zemon on 2008-01-24
More data: If I hook up the projector and restart X, I get the login screen as described above (displayed on both the internal screen and the projector). If I unhook the projector and log in, all is well, except that I have some extra background displaying below the bottom menu bar. X is, indeed, running at 1280x800. I can then reconnect the projector and see stuff in both places... but the projector is at 1280x720.

If I do anything which messes with the screen resolution, including booting a VMware virtual machine, both screens go black.

Ideas???

Thanks,
-- Art Z.

---

