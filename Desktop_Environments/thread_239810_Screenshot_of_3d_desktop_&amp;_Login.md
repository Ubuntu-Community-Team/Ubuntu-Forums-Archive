---
title: "Screenshot of 3d desktop &amp; Login"
date: 2006-08-19
forum: Desktop Environments
---

### Post by Steve S. on 2006-08-19
I'm sorry to do this, 'cause I know it's posted, I just can't figure out the search parameters.

So, if you would please tell me how to get screenshots of things like 3ddesktop and the boot-up screen in action?  I'm sure there is some type of keyboard short cut or something but I just can't find it in the forums.

I can take screenshots of the current desktop once it's running, just don't know how to take those other shots to be able to show Windows friends of mine the 3d stuff and etc.

---

### Post by meng on 2006-08-19
There is a keyboard shortcut in GNOME (default I think is PrntScrn), but I'm not sure if it would work with the 3ddesktop transitions.
I suggest the easier way to achieve this one-off task would be to google for screenshots already posted by others. e.g.
[http://linuxreviews.org/features/3ddesktop/](http://linuxreviews.org/features/3ddesktop/)

I know this doesn't really answer the question, just another suggestion that's all.

---

### Post by kerry_s on 2006-08-19
Use gimp>file> acquire>screenshot, then just set the delay to how much time you need to get into 3ddesk. For the login i haven't got a clue, unless you run a system in qemu. I use a launcher for 3ddesk,see pic

---

### Post by Steve S. on 2006-08-20
> **kerry_s said:**
> Use gimp>file> acquire>screenshot, then just set the delay to how much time you need to get into 3ddesk. For the login i haven't got a clue, unless you run a system in qemu. I use a launcher for 3ddesk,see pic

Wow...great idea!  Never thought of that, kerry_s...I'll give it a shot!

Thanks for the input, all!

---

### Post by ardchoille on 2006-08-20
**To get a screenshot of the login screen:**

**1**. You'll need a command to take a screenshot of the GDM screen. I recommend making a bash script with the following content:

```

#!/bin/bash
chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/screenshot.png

```
Create a new file, enter the above contents into it, save it as gdmshot.sh and make it executable with: chmod a+x gdmshot.sh. Move gdmshot.sh to a place where you don't mind leaving it permanently.

**2**. Logout of your current session.

**3**. When the gdm screen appears, press the following keys:

CTRL+ALT+F2

to go to console 2.

**4**. Login as yourself.

**5**. Type in the following:

```

sudo sh /path/to/gdmshot.sh

```

**6**. Wait 5 seconds and your screenshot will be stored at /tmp/screenshot.png

I use this method to get screenshots for the GDM themes I create. Here's the script I use for GDM screenshots:

```

#!/bin/bash

# take a gdm screenshot
chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/screenshot.png

# change owner and group ownserships of the screenshot
chown username:username /tmp/screenshot.png

# move the screenshot to a more suitable palce
mv /tmp/screenshot.png /home/username/screenshot.png

```

Remember to replace the "username" above with your user name.

---

### Post by Steve S. on 2006-08-21
> **ardchoille said:**
> **To get a screenshot of the login screen:**

**1**. You'll need a command to take a screenshot of the GDM screen. I recommend making a bash script with the following content:

```

#!/bin/bash
chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/screenshot.png

```
Create a new file, enter the above contents into it, save it as gdmshot.sh and make it executable with: chmod a+x gdmshot.sh. Move gdmshot.sh to a place where you don't mind leaving it permanently.

**2**. Logout of your current session.

**3**. When the gdm screen appears, press the following keys:

CTRL+ALT+F2

to go to console 2.

**4**. Login as yourself.

**5**. Type in the following:

```

sudo sh /path/to/gdmshot.sh

```

**6**. Wait 5 seconds and your screenshot will be stored at /tmp/screenshot.png

I use this method to get screenshots for the GDM themes I create. Here's the script I use for GDM screenshots:

```

#!/bin/bash

# take a gdm screenshot
chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/screenshot.png

# change owner and group ownserships of the screenshot
chown username:username /tmp/screenshot.png

# move the screenshot to a more suitable palce
mv /tmp/screenshot.png /home/username/screenshot.png

```

Remember to replace the "username" above with your user name.

Ahhh...the epitome of open source: I get to learn something new!

Thanks ardchoille, I'll give it a shot!

---

### Post by Steve S. on 2006-08-28
Ok, ardchoille, I did what you suggested and your script worked great.

I now have a great shot of my login (see attachment).  I wanted to be able to do this, but I also wanted to be able to get a shot of my usplash screen (see attachment, Kubuntu).

Can you (or anyone) tell me how to do this?

---

### Post by mssever on 2006-08-28
> **kerry_s said:**
> Use gimp>file> acquire>screenshot, then just set the delay to how much time you need to get into 3ddesk. For the login i haven't got a clue, unless you run a system in qemu. I use a launcher for 3ddesk,see pic

kerry_s: Where did you get the launcher icon? I want it!

---

### Post by Steve S. on 2006-08-28
> **mssever said:**
> kerry_s: Where did you get the launcher icon? I want it!

Actually, kerry_s, I'd like to know that too, although that doesn't help me with my usplash shot.  I did get 3ddesk settup and now have a hot-key set for it...pretty cool stuff, but very cool icon.;)

---

