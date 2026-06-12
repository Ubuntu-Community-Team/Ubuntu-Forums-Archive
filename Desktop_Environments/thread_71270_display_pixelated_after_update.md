---
title: "display pixelated after update"
date: 2005-10-02
forum: Desktop Environments
---

### Post by pataphysician on 2005-10-02
i haven't updated anything in qute awhile. tonight i opened synaptic and was told there were 61 updates available, so i installed them and rebooted. after rebooting, my display is blurry or pixelated or a combination of the two. i only casually browsed the list of updates before proceding, so i don't know what was updated or what may be causing the problem. it looks like this now:

[http://home.swfla.rr.com/pataphysician/Screenshot.png](http://home.swfla.rr.com/pataphysician/Screenshot.png)

it's crisper if i drop the resolution down to 800x600, but i'd much prefer to keep it at the resolution i've been using. i'm going to try removing and reinstalling the nvidia-glx package, but figured i'd look for more experienced help in the meantime.

i'm running a toshiba laptop with an nvidia display adapter. if you need any more information, please ask! thanks.

---

### Post by pataphysician on 2005-10-02
problem appears solved. i uninstalled/reinstalled nvidia-glx, though i don't know if that was necessary. afterwards it was still blurry. i did *sudo nvidia-glx-config enable* and restarted x again, and things are ok now. if anyone else is having display issues after updating, try just issuing that command, and you'll probably be fixed up.

EDIT: now that my display is clear, it looks like my screenshot is clear, too. i guess the SS didn't capture what i was seeing...

---

