---
title: "[SOLVED] kpager problem"
date: 2007-11-09
forum: Desktop Environments
---

### Post by viking777 on 2007-11-09
After months of using compiz I have finally come to my senses and returned to using kwm as my desktop manager. My initial thoughts about compiz - that it was a complete waste of time and effort, have imho been fully justified by a few months usage, the only thing that it adds to the computing experience is added boot up time, something Ubuntu could well do without.

That decision made though I have come back to kwm and something seems to have changed. I always had the desktop pager applet in my system tray and still want it there, but now every time it starts up it loads a kpager window on my desktop as well as the tray applet in the tray. This never used to happen.

 I cant work out if this is supposed to happen or if it is some quirk of my system, but I do know two things - I don't want it there and having to close it every time is irksome.

Can anyone tell me how to rid myself of this annoying little window but still keep the pager applet in the tray?

---

### Post by viking777 on 2007-11-10
Well it looks like nobody else is having this problem or else you are all happy with that annoying little window starting up every time. 

I have actually deleted the pager completely from the system tray now as that is the only way I can find to stop the window loading. 

It is not my preferred solution  by any means, but it is the only workround I can come up with for now.

If anyone can tell me how to get back to the original behaviour where only the system tray pager applet loads I would still like to hear about it.

---

### Post by viking777 on 2007-11-10
Damn me, this is getting worse! This ruddy pager window is still starting up even though I have deleted the kpager applet from the tray!!

Where is it starting from?? I have absolutely nothing in ~/.kde/Autostart so where else could it start from?

---

### Post by viking777 on 2007-11-10
[SIZE="7"]**DOH**[/SIZE]

I found my answer, it has nothing to do with kpager, it is just me. I must have saved a kde session with the window open, that is why it kept on reappearing.

Close the window, save the session again and this time it is gone for good.

---

