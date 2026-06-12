---
title: "Need Icon displayed for startup application"
date: 2010-01-19
forum: Desktop Environments
---

### Post by harky on 2010-01-19
I have recently upgraded (via a clean install) to Karmic from Intrepid. I've only manually added one application (DavMail) to run on startup.

On Intrepid, when the application runs on startup, the icon shows on the panel in the right side (near the network connection icon, etc).  In Karmic, the same application does not show up, so I have no access to the application.  Interestingly, I did notice that it was there during one session, but only that one time.

Is there anywhere to set "show this on panel when running" or some similar config option?

Thank You.

---

### Post by tgeer43 on 2010-01-20
Just a guess here but perhaps your app is loading and attempting to display its icon in the notification area before the panel is fully initialized and ready to display it. Maybe try adding a 'sleep 5' to your application's startup command to give the panel a little more time to load and initialize.

Good luck,

tgeer

---

### Post by harky on 2010-01-22
Thanks.  That took care of it, although it wouldn't work with ```
sleep 10; /usr/bin/davmail
``` directly as the command for the startup application.  I could put it there, but the application didn't start. I'm not sure if it was the space between the ; and / but it was fine from a terminal.  So I created a bash script that did the same thing and put the script as the command and voila! it worked.

Thanks

---

