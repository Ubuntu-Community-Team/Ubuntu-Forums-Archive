---
title: "Show desktop/Fade to desktop &quot;hot corner&quot; in Compiz fusion?"
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by groo028 on 2007-06-22
I cant seem the find the right place to set a hot corner for the "Show desktop" or "Fade to desktop" plugins. Any ideas?

---

### Post by joeblow1102 on 2007-06-22
As far as my understanding goes, if you have the CompizConfig Settings Manager installed, if you go to General Options > Actions > General, Hide all windows and focus desktop would be what you're looking for.

---

### Post by groo028 on 2007-06-22
thank u :D that worked!

---

### Post by Duranxl on 2007-08-19
Ey all. i've been reading some of the threads here about the show desktop..and like here, all suggest "actions in general options"
But i don't have that :confused::confused:
I only have a "general" tab under general options..and i can only disable/enable "Show Desktop" ..i don't have any options for it!

thanks

edit: now i found it under "advanced search".. weird it doesn't show up in the normal general options ??
I have another question then: how can i change the shortkeys? e.g. i'd like to change ctrl+alt+d to super+D
Also how do I change the way yo initiate the cube? in beryl i could mouse3 click&hold and i could move around

---

### Post by nonragiono on 2007-08-24
hi Duranxl,
in a termina type 

gconf-editor

go in 

app - metacity - global_keybindings

and find 

show_desktop

change the value

 <Control><Alt>d 
to 
<Super>d

be happy.

see you.
nonragiono

---

### Post by NawaMan on 2007-08-26
Hi There, I have similar problem but the option in the General Option does not have any effect. I can set any corner to show Expo and Scale but not for Show Desktop. Show Desktop only work if I use Keyboard but that is not so conveninet :(.I use to use this in beryl and I love it. Any workaround is possible?

---

### Post by NawaMan on 2007-10-23
Someone found the work around: [http://ubuntuforums.org/showthread.php?p=3613233](http://ubuntuforums.org/showthread.php?p=3613233)

---

