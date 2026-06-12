---
title: "fsck'd up my .ICEauthority"
date: 2005-01-02
forum: Desktop Environments
---

### Post by Dylanby on 2005-01-02
Ok.

So I screwed up my .ICEauthority trying to get Doom 3 to run (of all things).

I tried (from failsafe terminal) to chown & chgrp, blah, blah. Didn't work.

So then I tried "sudo rm -rf /home/dylan/.ICEauthority", because I read that a new one would just be created in it's place. No dice.

I still have .ICEauthority-c & .ICEauthority-l files (with proper permissions). Should I just delete these also? At this point I'm a little leary of experimenting on my own.

---

### Post by Dylanby on 2005-01-02
Well I removed both .ICEauthority-c & .ICEauthority-l & I'm able to get back into Gnome.

---

### Post by valadil on 2005-01-31
As far as I can tell, all .ICEauthority ever does is stop you from logging into a DE via GDM.  I frequently have to remove it.

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=Dylanby]Ok.

So I screwed up my .ICEauthority trying to get Doom 3 to run (of all things).

I tried (from failsafe terminal) to chown & chgrp, blah, blah. Didn't work.

So then I tried "sudo rm -rf /home/dylan/.ICEauthority", because I read that a new one would just be created in it's place. No dice.

I still have .ICEauthority-c & .ICEauthority-l files (with proper permissions). Should I just delete these also? At this point I'm a little leary of experimenting on my own.[/QUOTE]

use 

gksudo 

instead of plain sudo next time to avoid that.

---

