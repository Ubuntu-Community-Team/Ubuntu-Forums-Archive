---
title: "autostart workspace 2"
date: 2005-07-18
forum: Desktop Environments
---

### Post by luckyaba on 2005-07-18
I am trying to get my firefox to autostart on desktop 2 but am having no luck figuring out how. Anyone have any ideas?

---

### Post by Caboto on 2005-07-19
There is a possibility, but it's not that easy (at least for a newbie like me :))... That problem is already discussed a bit at the [Warty](http://ubuntuforums.org/showthread.php?t=5315) Board.

You'll need [wmctrl](http://sweb.cz/tripie/utils/wmctrl/). It detects all open windows and you can get the Window ID. With that, you can simply move the corresponding window to the workspace you want.

I'm moving Firefox and Thunderbird right after Startup to Workspace 2 and 5. So I've added Firefox and Thunderbird to my Session plus a little bash script at the last possible session entry. My script looks like this:
```
#!/bin/bash
sleep 5
wmctrl -i -r `wmctrl -l | grep 'Mozilla Thunderbird' | awk '{print $1}'` -t4
wmctrl -i -r `wmctrl -l | grep 'Mozilla Firefox' | awk '{print $1}'` -t1
```
Need to hold back the script 5 seconds (with the sleep command), so that Firefox and Thunderbird are fully loaded. The t1 and t4 at the end are the Workspaces ([workspace number]-1).

Hope I could help you. I'm quite new to Linux myself.

---

