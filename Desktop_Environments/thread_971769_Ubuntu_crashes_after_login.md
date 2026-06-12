---
title: "Ubuntu crashes after login"
date: 2008-11-05
forum: Desktop Environments
---

### Post by shiznatix on 2008-11-05
Ok so I did a fresh install of Intrepid the other day and everything was going A-OK until just nowish. I hooked up another monitor and got the whole dual monitor thing working perfect with the "1 big desktop" instead of cloning and everything, twas awesome. I am using the ATI non-free drivers.

Then, all of a sudden as I was just going about my business not doing anything crazy (I was moving an icon on the desktop from 1 screen to the other) X crashed and sent me back to the login screen.

That sucked but oh well, re-login ya? Nope. Now when I try to login, gnome *almost* finishes loading but then bam, crashes to something like the advanced bootup screen that shows exactly what is happening. I can't do anything and it just sits at the line "Checking battery" or something similar. This is also strange because this is not a laptop I am using, the only battery in my computer is the clock battery.

I have tried restarting, booting in "fail safe gnome" mode, the works. Nothing. The only reason I can do this now is because I thankfully did not overwrite my previous install of ubuntu so I was able to boot into that.

I am at a loose here. What can I do to get my computer back?

---

### Post by shiznatix on 2008-11-05
ok after doing the "attempt to fix x server" and getting it boot up I got it working again, it seams like the ati drivers were the cause of problems. The problem is that I want to use them because I can't use compiz without them so after a bit of fighting it let me put compiz back on and use the ati drivers but I feel like this might happen again which sucks.

Is there a way to fix this? keep the drivers from crashing everything and making me very angry?

edit: ya happened again in about 3 minutes. For anyone else having this problem boot the recovery mode kernel, select "try to fix x server" then boot normally, then when you login you should be using the open source drivers and then you can change your screen to be 1 big desktop instead of a mirror. I still want to use the ATI drivers though so I can play games and whatnot...

---

### Post by ram130 on 2008-11-05
same problem here  but under different circumstances. I am not running a dual monitor setup or ATI graphics, but rather Nvidia. Sometimes when i am work in ubuntu or talk on skype, It just Freezes leading me to hard restart it and make it check for errors. Then after its done and i am doing a normal boot it freezes after user name and password is entered and u just about to see da desktop. Its  been happening since i installed 8.10(clean), its very unstable. Ubuntu 8.04 was very smooth with no freezes. Why is this happening now?:confused:

---

