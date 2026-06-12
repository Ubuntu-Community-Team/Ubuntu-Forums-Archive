---
title: "Startup script for turning monitor off and on"
date: 2012-10-01
forum: Desktop Environments
---

### Post by siXor on 2012-10-01
Hi!

So this is a problem for me since I have two monitors for my Ubuntu Desktop. I'm running Ubuntu 12.04.

Ok, so first when I installed Ubuntu I had this problem with enabling the second monitor but not at the same time mirroring the two monitors. It did not now how to meet the required resolution. I searched for an answer and got one fixing my problem. I simply edited my xorg.conf file and added a virtual size for my desktop, now with the virtuyal resolution of 3840 1080. Log out and back in and it works like a charm and I could now use both of my monitors.

But, then after a few reboots the secondary screen started to act weird. Like, when I pull som window over to that screen, the contours sticks and it looks really strange. So to have it acting normal I have to go to the top right "start button" -> Displays... -> Select secondary monitor -> Turn it of -> Apply -> Keep Configuration -> Turn it on -> Apply -> Keep Configuration.

As you can imagine this is a little annoying and therefor it would be awsome if I could make a script that does this at every startup. 

Hope you guys understand what I want to accomplish.

Thanks in advance! :)

---

