---
title: "trackerd not autostarting"
date: 2010-05-12
forum: Desktop Environments
---

### Post by jazzgossen on 2010-05-12
I'm having problems getting tracker start automatically when I log in. However, if I execute /usr/lib/tracker/trackerd manually, all is well.

I have both tracker and tracker-applet ticked in Preferences/Sessions. However, after a clean boot, tracker is unavailable: "pgrep -l tracker" shows that tracker-applet is running but no trackerd, and when using tracker-search-tool I get the error message "Could not connect to search service as it may be busy".

Looking at the syslog, I have this entry saying that trackerd doesn't exist:

> May 12 09:38:41 lateralus gnome-session[2104]: WARNING: Could not launch application 'trackerd.desktop': Unable to start application: Misslyckades med att köra barnprocessen "trackerd" (Filen eller katalogen finns inte)

I have two trackerd.desktop files: /etc/xdg/autostart/trackerd.desktop and /usr/share/autostart/trackerd.desktop. They are identical, and refer to /usr/lib/tracker/trackerd, which does indeed exist.

Any other things I could try to see why it doesn't autostart?

---

### Post by Antronin on 2010-08-29
I have exactly the same problem. Could anyone shade light what I can do to have trackerd back to business?
My other users have it up and running when logging in so something must be in my own config screwed up, but don't know what to search for.

---

