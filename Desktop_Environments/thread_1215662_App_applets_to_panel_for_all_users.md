---
title: "App applets to panel for all users"
date: 2009-07-17
forum: Desktop Environments
---

### Post by WinDevil on 2009-07-17
Hi all,

I am trying to add the "diskmount" applet for all the users. I am sure that there is some way of doing this. I can't seem to get the parameters rigth. Besides, there are so many config files, I am not sure which one is right.

I use this command (as root):
```

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --set /apps/panel/default_setup/general/applet_id_list -t list --list-type=string "[drivemount,mixer,fast-user-sw
itch-applet,clock,notification_area,show_desktop_button,window_list,workspace_switcher]"

```Any help would be highly appreciated.
Thanks.


To put this differently:

Where can I modify the default list  of applets on gnome-panel for all the users? I want that a particular applet shows on the panel of any/all the users when they log in.

---

