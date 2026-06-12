---
title: "Applications lockup and fail to start after wine?"
date: 2008-06-26
forum: Desktop Environments
---

### Post by Azzuron on 2008-06-26
Hey folks. I have run into an odd problem, im not sure exactly what is causing it, but i think it has to do with wine.

Situation is this, i was playing a little wow in wine the other night, i closed out went to bed today i come to my PC and FF3 won't start up. There is a process but no gui. so i killed it and tried again, same thing. so i rebooted and everything was ok. figured it was a fluke thing. so today i play wow again, and after i close out i tried FF again to get on the webs and nothing. same problem. I tried the close the process again and start but nothing. So, i tried to get a terminal... window pops up but stops responding immediately. Curiously i tried to load wine/wow again and it came up fine. Also Pidgeon seemed to crash on me at one point tonight while all this is happening, but loaded back up ok. its very bizzare and im not sure how to troubleshoot this issue, other than to never use wine again and see if it keeps happening without wine, but then i still don't know what to look at next. Thanks for any assistance the great ubuntu minds can provide.

---

### Post by p_quarles on 2008-06-27
I've noticed Wine will occasionally leave behind a runaway process that can mess things up. From what I've seen, it just eats CPU time, but I still wonder if you're experiencing something similar. 

Does your system monitor bear out anything that might confirm this hunch?

---

### Post by Azzuron on 2008-06-27
Generally no. I did find a rogue process from wineserver, but i chopped it and the problem still persisted. I am starting to wonder if this issue might relate back to hardware. When i put this system together, i had a hell of a time getting the ram configuration correct. This board and ram combo were very funny. System seems very stable though, other than that issue, and applications do not crash they just get that lockup issue. I should run memtest again i guess, and maybe some HDD checks maybe somethings funky there.

---

### Post by seveninchbread on 2008-07-02
I am having the same problem, and there is nothing weird about my system; so I don't think it's related to your hardware setup.

---

