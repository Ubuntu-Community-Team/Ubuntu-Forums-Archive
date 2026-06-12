---
title: "Ubuntu forget my preferences"
date: 2011-06-28
forum: Desktop Environments
---

### Post by rezluvr on 2011-06-28
Hi board.
I recently installed Ubuntu 10.10, and as i am not much for fancy visuals, i went to System > Preferences > Appearances to set Visual effects to "None".
After a restart it had set it back to the default, normal. Not a big deal, but a bit strange i thought. For several days i tried to change it, and each time, after restart it went back to default. Now i had the last two days, that not only does it keep the visual to normal, it also boots with a different Theme, than what i normally use. That is quite annoying, and this led me to now seek advise here. Any suggestions, or anything i can look up in the console, to tell you more relevant information?
Thanks for the help!

---

### Post by Krytarik on 2011-06-28
For your first issue:

Check in Gconf if Metacity is enabled to run at startup:

- press Alt+F2
- enter "gconf-editor"

- browse down to "/desktop/gnome/session/required_components/windowmanager"
- "metacity" should be stated there
- the value for Compiz would be "compiz"

- browse down to "/desktop/gnome/applications/window_manager"
- "/usr/bin/metacity" should be stated in both "current" and "default"
- the value for Compiz would be "/usr/bin/compiz"

__________________________________________________

For your second issue:

It's a common bug:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

Threads with summed-up workarounds:
[http://ubuntuforums.org/showthread.php?t=1722179](http://ubuntuforums.org/showthread.php?t=1722179)
[http://ubuntuforums.org/showthread.php?t=1724702](http://ubuntuforums.org/showthread.php?t=1724702)

Hope this helps!

---

### Post by rezluvr on 2011-06-29
Thanks for the guidelines, but i am still not fully operational here. I can get to the gconf-editor fine, and find the path "/desktop/gnome/session/required_components/windowmanager"
where i have a set of "Name" and "Value" looking like this:
___Name   -   Value___
filemanager   -    nautilus
panel   -    gnome-panel
windowmanager   -    metacity

there is no mention of compiz here.

I can find the path "/desktop/gnome/applications/window_manager"
Here i have 4 lines divided in to set "Name" and "Value"

___Name   -   Value___
current   -   /usr/bin/compiz
default   -   /usr/bin/compiz
number_of_workspaces   -   <no value>
workspace_names   -   <no value>

So, what is it i miss then? 
Thanks for the help so far, and the time to look at it again!

---

### Post by Krytarik on 2011-06-29
> **rezluvr said:**
> 
I can find the path "/desktop/gnome/applications/window_manager"
Here i have 4 lines divided in to set "Name" and "Value"

___Name   -   Value___
current   -   /usr/bin/compiz
default   -   /usr/bin/compiz
number_of_workspaces   -   <no value>
workspace_names   -   <no value>

So, what is it i miss then? 

Answer ;-) :
> **Krytarik said:**
> 
- browse down to "/desktop/gnome/applications/window_manager"
- **"/usr/bin/metacity" should be stated in both "current" and "default"**
- the value for Compiz would be "/usr/bin/compiz"


---

### Post by rezluvr on 2011-06-29
so one last question, and i think i am good then. SHould i add a Compiz name and value, since i now replaced the  default and current with the /usr/bin/metacity value. And if so, what type should i add it as then?
The second thing worked out after a reboot, so it seems that the theme is good now!

---

### Post by Krytarik on 2011-06-29
> **rezluvr said:**
> so one last question, and i think i am good then. SHould i add a Compiz name and value, since i now replaced the  default and current with the /usr/bin/metacity value. And if so, what type should i add it as then?
No, there is only one set of those keys possible and, obviously, either key can only host one value at a time. So, if you want to change the window manager in future, you have to change those values again.

---

