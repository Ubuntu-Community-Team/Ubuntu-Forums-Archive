---
title: "getting lg3d running in Ubuntu?"
date: 2006-03-10
forum: Desktop Environments
---

### Post by issueperson on 2006-03-10
continuing from the 3d topic:


i got everything installed for lg3d.  i think.
i keep getting this error when i try to run ./lg3d-app
----------------------------
brady@llama:/opt/lg3d/bin$ sudo ./lg3d-app
Password:

Starting up Project Looking Glass...

Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!

Fatal server error:
could not open default font 'fixed'
[1] 10001
access control disabled, clients can connect from any host

-----------------------------

if anyone knows what's up... please let me know.  I'm not exactly a newb, but i'm not the weathered veteran of linux that some of the people on here are.
issueperson

---

### Post by dcstar on 2006-03-10
[QUOTE=issueperson]continuing from the 3d topic:


i got everything installed for lg3d.  i think.
i keep getting this error when i try to run ./lg3d-app
.......
if anyone knows what's up... please let me know.  I'm not exactly a newb, but i'm not the weathered veteran of linux that some of the people on here are.
issueperson[/QUOTE]
As far as I can see this is still a developmental package, and the Ubuntu stuff is even more immature:

[https://lg3d-core.dev.java.net/binary-builds.html](https://lg3d-core.dev.java.net/binary-builds.html)

---

### Post by issueperson on 2006-03-10
i have lg3d installed on my sessions menu now...

when i start it up, i just get a black screen.

also, when i'm in gnome and start up /usr/share/lg3d/bin/lg3d-dev it starts up and i just get a black window open.

anyone else have that problem before?  what'd you do?

---

