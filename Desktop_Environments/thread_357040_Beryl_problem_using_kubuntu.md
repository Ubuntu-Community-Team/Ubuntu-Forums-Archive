---
title: "Beryl problem using kubuntu"
date: 2007-02-09
forum: Desktop Environments
---

### Post by paolo17 on 2007-02-09
I used this guide to install beryl 
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL) 

made this change also mentioned there 
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer -dpi 96 & 

and this one 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)" 
xauth -i add :1 . "$cookie" 

made a new session with xgl name also 


used the pc for one day, i rebooted and did some updates with adept manager. 

After a adept manager update (one single library was updated during this update) i rebooted and get: "Could not open network socket please check that the dcopserver program is running."

trying to start the dcopserver manually returns an error:

"ICE Default IO Error Handler doing an exit(), pid=5280 errno=2"
 

I am now able to use konqueror sudo mode after some alterations but my knowledge gets me that far.

---

### Post by ingo on 2007-02-10
Just sifting through unanswered mails - your query may be too specific for Ubuntu, try the beryl forum instead as they are both very helpful and knowledgeable. And, of course, feel free to write up your solution here :smile:

---

### Post by paolo17 on 2007-02-11
bump, help me on this guys anyone who's familiar, thanks.

---

