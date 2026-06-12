---
title: "plasma-desktop workaround"
date: 2014-09-13
forum: Desktop Environments
---

### Post by mattdawolf on 2014-09-13
My plasma-desktop continually crashes. While I haven't been able to track down the cause, I tried putting plasma-desktop in crontab to run every minute as a workaround. crontab just ignored it. I entered its path, still nothing. I then made a shell script to execute "kstart plasma-desktop" which works in konsole but crontab doesn't care about that either. 

Is there anything I'm overlooking? Can anyone recommend the best way to do this workaround in the meantime?

---

