---
title: "[HOWTO]Disable panel applets globally"
date: 2009-03-05
forum: Desktop Environments
---

### Post by hayalci on 2009-03-05
Gnome adds some default applets to your panel when you first login. In our environment with 8.04 LTS, fast-user-switch applet was querying remote server for ALL user names. Because of this, logging in took about 20-25 seconds. If fast-user-switch applet was disabled the time was 2-3 seconds at most.

 If you want to disable panel applets globally use the following steps. Be warned that this only applies to users who log in the first time after you do this setting. **I would be grateful, If anyone can explain how to remove applets from all previously logged in users.**

[LIST]
[*]Get the default applet list with the following command
```

gconftool-2 --direct --config-source xml:readonly:/var/lib/gconf/debian.defaults --get /apps/panel/default_setup/general/applet_id_list

```
[*]Remove the applet you don't want from that list.
[*]Set new default applet list with the following command
```

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --set /apps/panel/default_setup/general/applet_id_list -t list --list-type=string "[mixer,clock,notification_area,show_desktop_button,window_list,workspace_switcher,trashapplet]"

```
[/LIST]

You can automate the above operation with 
```

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --set /apps/panel/default_setup/general/applet_id_list -t list --list-type=string $(gconftool-2 --direct --config-source xml:readonly:/var/lib/gconf/debian.defaults --get /apps/panel/default_setup/general/applet_id_list | sed "s|fast_user_switch||" | sed "s|,,|,|g"  | sed "s|\[,|\[|" | sed "s|,]|]|")

```

I have found [this page (Customising Gnome Panel)]("http://web.archive.org/web/20071106001420/http://www.byteclub.net/wiki/GnomePanel") and [this page(Script for Removing GNOME Panel Applets)]("http://machine-cycle.blogspot.com/2007/11/script-for-removing-gnome-panel-applets.html") as helpful tips, and source of the huge one liner command above.

/rambling mode on
It's a shame that there is not a gconftool option to append/remove items to/from a list. Also, I seem to HATE HATE HATE gconf and gnome more by each passing day.

---

### Post by C-- on 2009-03-05
You can also use Sabayon, which is a graphical front end for gconf.

[http://www.linux.com/feature/114319](http://www.linux.com/feature/114319)

---

### Post by WinDevil on 2009-07-20
Is there some similar command to "enable" an applet globally for all users? I tried adding the applet name to the list but it doesn't work. 

Thanks for any help.

---

### Post by MikeDK on 2010-05-24
Hi having serious problems on adding the fast_user_switch applet to my gnome-panel after removing it, how do i add it back into the panel??

kind regards mikedk
using lucid 10.04

---

### Post by spezticle on 2010-06-15
> **hayalci said:**
> Gnome adds some default applets to your panel when you first login. In our environment with 8.04 LTS, fast-user-switch applet was querying remote server for ALL user names. Because of this, logging in took about 20-25 seconds. If fast-user-switch applet was disabled the time was 2-3 seconds at most.

 If you want to disable panel applets globally use the following steps. Be warned that this only applies to users who log in the first time after you do this setting. **I would be grateful, If anyone can explain how to remove applets from all previously logged in users.**

[LIST]
[*]Get the default applet list with the following command
```

gconftool-2 --direct --config-source xml:readonly:/var/lib/gconf/debian.defaults --get /apps/panel/default_setup/general/applet_id_list

```
[*]Remove the applet you don't want from that list.
[*]Set new default applet list with the following command
```

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --set /apps/panel/default_setup/general/applet_id_list -t list --list-type=string "[mixer,clock,notification_area,show_desktop_button,window_list,workspace_switcher,trashapplet]"

```
[/LIST]

You can automate the above operation with 
```

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --set /apps/panel/default_setup/general/applet_id_list -t list --list-type=string $(gconftool-2 --direct --config-source xml:readonly:/var/lib/gconf/debian.defaults --get /apps/panel/default_setup/general/applet_id_list | sed "s|fast_user_switch||" | sed "s|,,|,|g"  | sed "s|\[,|\[|" | sed "s|,]|]|")

```

I have found [this page (Customising Gnome Panel)]("http://web.archive.org/web/20071106001420/http://www.byteclub.net/wiki/GnomePanel") and [this page(Script for Removing GNOME Panel Applets)]("http://machine-cycle.blogspot.com/2007/11/script-for-removing-gnome-panel-applets.html") as helpful tips, and source of the huge one liner command above.

/rambling mode on
It's a shame that there is not a gconftool option to append/remove items to/from a list. Also, I seem to HATE HATE HATE gconf and gnome more by each passing day.

i'm sharing your growing hate for gnome and gconf.
this doesn't work in karmic.

---

