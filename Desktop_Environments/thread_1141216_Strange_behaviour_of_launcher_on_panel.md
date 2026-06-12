---
title: "Strange behaviour of launcher on panel"
date: 2009-04-28
forum: Desktop Environments
---

### Post by codemind.org on 2009-04-28
Ok, I've got such script to run my conky:
```
#!/bin/bash
# start conky
DIR=/home/codemind/.conky/
conky -c "$DIR"config_main &>/dev/null &
conky -c "$DIR"config_lastfm_top &>/dev/null &
conky -c "$DIR"config_lastfm_week &>/dev/null &
conky -c "$DIR"config_lastfm_recent &>/dev/null &

```And when I'm running it by console or by lanucher on desktop all works fine. But when I put lanucher on gnome-panel something goes wrong - windows are staring in random order and not always all of them (sometimes 1, 2, 3 or all 4). What's wrong with launchers on gnome-panel?

---

