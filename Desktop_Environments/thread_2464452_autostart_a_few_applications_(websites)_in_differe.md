---
title: "autostart a few applications (websites) in different size sorted on the desktop"
date: 2021-07-02
forum: Desktop Environments
---

### Post by bj45656 on 2021-07-02
Hello,

I want to start some websites but want to see them alle at once on the desktop. I don't know what exactly I should searching for so I start asking here. I found gTile to create a grid and put applications to different positions. But I'm looking for a solution to recover the desktop alert reboot.

I have a smart home and I want to use a raspberryPi to show some infos on a monitor. The infos are from some websites and I want to see all websites at once. For now it would be enough to see 3 windows. One windows on the left side of the screen and 2 windows on the right side among themselves.

Does anyone know a software to create a splitted desktop which recover windows after a reboot. Or is there an command to start a windows in one of the gTile (or other software) virtual desktop?

Sorry for my english. Hope you understand me.

Thanks!

Alex

---

### Post by ActionParsnip on 2021-07-02
devilspie may be able to help too

---

### Post by TheFu on 2021-07-02
I would just create an index.html file that had iframes for each of the websites on a single page, using the layout I want.  Then launch the browser in full-screen mode - most of the time that can be toggled using F11.  From a startup, it can be requested with ... let me look it up:

```
#!/bin/bash
/usr/bin/chromium-browser  --allow-file-access-from-files ~/Presentations/index.html &
sleep 3;  # allow a few seconds for the browser to open.
/usr/bin/xdotool  search --sync --onlyvisible --class "Chromium" windowactivate key F11
```

Don't know if this works with Wayland or not.

---

