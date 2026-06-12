---
title: "How I can removing  gdesklets display by console?"
date: 2005-06-07
forum: Desktop Environments
---

### Post by lizardking on 2005-06-07
**How I can removing  gdesklets display by console?** Because I unsuccesful install a gdesk display and I can view it ont the screen so I cannot remove. This is my list of gdesk display:
```
lizardking@iac:~ $ gdesklets list
Currently open displays in profile "pippo":

/usr/share/gdesklets/Displays/starterbar-desklet-0.31.3/starterbar.display
/usr/share/gdesklets/Displays/GoodWeather/GoodWeather.display
/usr/share/gdesklets/Displays/clock-desklet/plainclock.display
/usr/share/gdesklets/Displays/extern-ip/ExternIP.display
/usr/share/gdesklets/Displays/lt-pager/LTPager.display
/usr/share/gdesklets/Displays/rss-grab/LTrssgrab.display
/home/lizardking/Desktop/rssticker.tar.gz_FILES/RSSTicker/rssticker.display
``` 

I wanto to remove the last one: **/home/lizardking/Desktop/rssticker.tar.gz_FILES/RSSTicker/rssticker.display** 

**How I can do this not in graphical mode ???**

_*in the man there is no command like this:  **gdesklets remove file.display option***_

---

### Post by tread on 2005-06-07
Check the contents of the .gdesklets directory in your home ..

---

### Post by lizardking on 2005-06-07
[QUOTE=tread]Check the contents of the .gdesklets directory in your home ..[/QUOTE]
```
^[[Alizardking@iac:~ $ gdesklets list
Currently open displays in profile "pippo":

/usr/share/gdesklets/Displays/starterbar-desklet-0.31.3/starterbar.display
/usr/share/gdesklets/Displays/GoodWeather/GoodWeather.display
/usr/share/gdesklets/Displays/clock-desklet/plainclock.display
/usr/share/gdesklets/Displays/extern-ip/ExternIP.display
/usr/share/gdesklets/Displays/lt-pager/LTPager.display
/usr/share/gdesklets/Displays/rss-grab/LTrssgrab.display
lizardking@iac:~ $
``` 

**Thank U very Much, ubuntu friend!!!**

---

