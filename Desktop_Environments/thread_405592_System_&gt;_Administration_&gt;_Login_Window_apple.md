---
title: "System &gt; Administration &gt; Login Window applet - asks for password, then disappears."
date: 2007-04-09
forum: Desktop Environments
---

### Post by tjod on 2007-04-09
Hi all;

Running 6.10 with Gnome. Tried KDE, then removed it as  I preferred the GDM. 

At some point a while after removing KDM, the Shutdown and Reboot icons disappeared from the panel where they normally appeared when clicking the Quit Icon

Now, the login Windows is different (back to an odd Gnome with an foot image and different colors than I had before.)

When I try to investigate this,  via System > Administration > Login Window applet -  I am asked for password,  the small Login Window icon appears in the Taskbar, then winks out & disappears. 

Any thoughts on how to get the applet and Shutdown / Reboot icons back? 

Thanks!
.

---

### Post by aysiu on 2007-04-10
Go to Applications > Accessories > Terminal and type ```
gksudo gdmsetup
``` If any errors appear, copy and paste them into a post in this thread.

---

### Post by tjod on 2007-04-10
Thanks for the fast reply.

gksudo gdmsetup produces: 

$ gksudo gdmsetup
GTK Accessibility Module initialized
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.

---

### Post by aysiu on 2007-04-10
Maybe [this](http://ubuntuforums.org/showthread.php?p=2275159) might help? It's worth a shot.

---

### Post by tjod on 2007-04-10
That did not appear to change anything,

On running the dpkg-reconfigure gdm, I received a message: 

[COLOR="Red"]invoke-rc.d:initscript gdm action "reload" failed.[/COLOR]

There did not seem to be any more or less problems - just no net effect. 

Thanks for the ideas though.  8-)

---

### Post by aysiu on 2007-04-10
I did [a Google search on your error](http://www.google.com/search?hl=en&q=%22Failed+to+connect+to+socket%2C+sleep+1+second+and+retry%22&btnG=Google+Search), and none of the results seem to contain a verified solution.

Not sure what to do.

---

### Post by tjod on 2007-04-10
This happened once before and I was about to reinstall anyway, so I didn't think too much of it.   There seems to be a fair number of the initial symptom being posted though (i.e. Quit button no longer shows shutdown or reboot on following panel...) 

 I've seen some references to possible association with "updates" though I can't report that with any high degree of correlation in this case. 

I'll keep looking around, and perhaps file a bug report.if I can catch it and box it up. 8-)

Thanks for the replies.

Tim O

---

