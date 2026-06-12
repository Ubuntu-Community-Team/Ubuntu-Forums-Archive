---
title: "How to Disable Locked Screen completely"
date: 2012-07-12
forum: Desktop Environments
---

### Post by wilsonmak on 2012-07-12
**Locked Screen after xdotool installation** 			
 			 			 		   		 		 		I am using MyTVbuntu 10.10 for an application that displays video and image.
But suddenly it locked itself with Login screen (/usr/bin/gnome-session --autostart=/usr/share/gdm/autostart/LoginWindow)
I have already disabled Screen Saver and lock screen capability on the desktop (XFCE4)
And set the followings:

1) xorg.conf
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"

2) /etc/kbd/config
BLANK_TIME=0
BLANK_DPMS=off
POWERDOWN_TIME=0

3) xscreensaver has been removed.

Just wondering what other config files trigger this lock screen function.
Or can I just rename /usr/bin/gnome-session ?

P.S.  Before I install xdotool, it was working properly.

Thanks,
Wilson

---

