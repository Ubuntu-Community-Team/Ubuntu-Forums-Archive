---
title: "[SOLVED] File manager not working with xgl"
date: 2007-11-20
forum: Desktop Effects &amp; Customization
---

### Post by patryk77 on 2007-11-20
Hello,

I have just installed XGL and compiz yesterday using Ubuntu 7.04.

After updating to 7.10, the desktop is no longer working, and neither is the file manager.

I can see my background image, but if I right-click on the desktop, I don't get a menu, nor do I see my desktop icons (the only ones were for my hard drives).

Also, if I go into the Places menu, nothing opens. The only activity I see is when I try to open my Computer. It says "Starting Computer" on the taskbar, but then that disappears without actually opening it.

Using:
Ubuntu 7.10
Proprietary ATI Accelerated Graphics drivers (everything was messed up with the OSS ones)
Sapphire Radeon X1600 Pro with 512 MB
Gnome 2.20.1

Thanks for your help :)

Edit: In the System Monitor / Processes I have a bunch of sleeping nautilus processes.
Tooltip says: "nautilus --no-desktop file:///{locations}"

{locations} correspond to the Places I tried opening

I tried running it from a terminal window, and this one says:
"nautilus --no-default-window -sm-client-id default2"z

Edit 2: I also have a compiz.real process with an argument of "--ignore-desktop-hints"

Hmmm... for some reason rebooting did the trick

Now I just need to enable openGL rendering

---

