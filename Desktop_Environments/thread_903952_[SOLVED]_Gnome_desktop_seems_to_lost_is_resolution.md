---
title: "[SOLVED] Gnome desktop seems to lost is resolution"
date: 2008-08-28
forum: Desktop Environments
---

### Post by dokter on 2008-08-28
Hi guys,

I'm running on Hardy Heron, on a Dell D820 laptop, graphic card is an Intel 945GM...

I've tried to do a dual screen desktop to have a big desktop on my laptop... 

I've modified xorg.conf to get a bigger virtual desktop for xrandr, I added these lines in xorg.conf:

        SubSection "Display"
                Virtual 3360 3360
        EndSubSection

I restarted my X <Ctrl+Alt+backspace> it worked, in part... I had a dual screened desktop but was not satified with the performance (video card limitation), so I edited back the xorg.conf to put it back at what it was...  restarted X... 

Since then, I'm back on a 1680x1050 desktop, but I don't see my AWN dock and my compiz desktop effect are not working anymore... But when I check open windows, I've my old firefox running, ducked somewhere, plus ps -ef | grep awn show me that it's running... I just can't see it anymore... 

Any ideas?

---

### Post by dokter on 2008-08-28
lol... should I've thought about it earlier... I re-enabled the advance desktop effect:

Menu> System> Preference> Appearance> Visual Effect

Everything is fine now!! :lolflag:

---

