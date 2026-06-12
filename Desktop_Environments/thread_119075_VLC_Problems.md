---
title: "VLC Problems"
date: 2006-01-18
forum: Desktop Environments
---

### Post by DigitalDuality on 2006-01-18
I managed to turn on the "skins" option for VLC as i loathe the default appearance of it and it went to it's default Mac looking skin that i'm somewhat used to but don't really like either...

except, the original window never went away. So then i had, two control panels to chose from..the default.. and whatever that skin is called.  Every single time i load VLC now, it freezes up my system.  I can't even load it long enough to turn the skin off before the system completely locks up and i can't even Ctrl Alt Bckspc

So i marked for uninstallation through Synaptic, and chose completely remove.  Then re-installed it and tried again.. and it's right back to where i was before.

Anyone else come across this problem?

---

### Post by dustigroove on 2006-01-31
I had this exact same issue.

Open the configuration file (should be **~/.vlc/vlcrc**) and delete the string *below* **Last skin used**. Then save the file and re-launch VLC, you should be all set.

---

