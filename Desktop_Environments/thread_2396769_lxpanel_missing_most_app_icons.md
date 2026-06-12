---
title: "lxpanel missing most app icons"
date: 2018-07-20
forum: Desktop Environments
---

### Post by liam.gutierrez on 2018-07-20
I tried using almighty Google to solve my problem of app icons missing on my lxpanel.

I used to have MegaSync, Diodon (clipboard manager), Bitcoin wallet, and an emoji picker as icons on my lxpanel. Not sure if they're supposed to be in the system tray but all those app icons were next to my nm-applet and power manager.

I also tried the script below I found on [https://wiki.lxde.org/en/LXPanel#Fix_empty_menu_in_LXPanel:](https://wiki.lxde.org/en/LXPanel#Fix_empty_menu_in_LXPanel:)
```
#!/bin/bash

killall lxpanel
find ~/.cache/menus -name '*' -type f -print0 | xargs -0 rm
lxpanel -p LXDE &
```

Unfortunately, this script didn't help much. It only changed the color of the panel and the menu icon but the other app icons are still missing.

Thanks for your help in advance.

---

