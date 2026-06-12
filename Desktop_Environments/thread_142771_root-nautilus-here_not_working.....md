---
title: "root-nautilus-here not working...."
date: 2006-03-11
forum: Desktop Environments
---

### Post by dermotti on 2006-03-11
I did some updates this weekend on my system and now my "root-nautilus-here" script is really flakey. It only seems to work after a fresh reboot, then after a few hours it doesnt work. Any ideas?

foo=`gksudo -u root -k -m "enter your password for nautilus root access" /bin/echo "got r00t?"`
sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI

---

