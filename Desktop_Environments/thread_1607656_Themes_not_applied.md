---
title: "Themes not applied"
date: 2010-10-28
forum: Desktop Environments
---

### Post by farbror_ace on 2010-10-28
Each time I boot my fresh install of Maverick Gnome starts with no skin at all.

To get the selected skin applied I have to run the following script:

#!/bin/bash
killall -9 gnome-settings-daemon
sleep 1
gnome-settings-daemon
rm -vr ~/.gconf/apps/nautilus
sleep 1
killall nautilus

After this my theme is applied and works for the rest of the session.

Its not the end of the world but still Id like to find out why I have to do this.
Anyone have any ideas?

---

