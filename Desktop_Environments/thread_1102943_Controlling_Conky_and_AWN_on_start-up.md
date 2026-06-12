---
title: "Controlling Conky and AWN on start-up"
date: 2009-03-22
forum: Desktop Environments
---

### Post by Another Monkey on 2009-03-22
I have been trying to get conky and AWN to launch after I login.  I tried adding them both to System/Preferences/Sessions/Startup Programs; conky seems to start too "early" (gets partially covered by the task ar when that appears) and AWN not at all.  I could see no way of controlling the startup order.

So I wrote a small script and placed in under /homer/<my name>
```
#!/bin/bash
sleep 20 && conky -d &
sleep 10 && avant-window-navigator &
```

And added that to startup Programs.

Conky and AWN seem to start OK, but the script appears to have slowed down the login process.  Or maybe I am just imagining that.

Is there a better way to accomplish getting AWN and conky to start on login?  A different script or location I should use?  I am using 8.10 with compiz-fusion.

Thanks.

---

### Post by FrederickUK on 2009-03-22
for conky, try setting the gap_x and gap_y switches in your .conkyrc file.

I've got mine set to gap_x 12 gap_y 35 and conky to start just by calling "conky" in sessions, seems to work fine. It sits just below the top gnome bar and never moves from that position.

Can't help with AWN though. I briefly tried using it myself but encountered almost the same problem (being that the taskbar covered the AWN dock)

hth :)

---

### Post by Another Monkey on 2009-03-22
Thanks, I'll try your conky settings (I want to play around with them anyway, tweak the border etc).

As for AWN...not sure I am sold on it, just trying it out.  Seems to be a great way to lose screen real estate (I removed the lower kicker bar as I was using AWN).

---

