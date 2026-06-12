---
title: "tearing w/compiz. how do I enable vsync w/ ATI card?"
date: 2006-06-13
forum: Desktop Environments
---

### Post by ACGarib on 2006-06-13
Hi, I just installed linux for the first time!! :D 

Now for my question,

I set up xgl/compiz and it works, but there is a pretty bad tearing problem. I have the fglrx driver for my ATI radeon 9800 pro and I think it is set up correctly. (w/ glxgears, I get around 9000 fps)

I read that installing driconf and enabling vsync fixes the problem, but after I installed driconf, it  gives me the error "could not detect any configurable direct-rendering capable devices. DRIconf will be started in expert mode" It then starts in expert mode instead of the regular mode and I dont know what to do.

I already enabled vsync in via aticonfig, but that did not help.

I also tried to use fireglcontrolpanel, but I get the error "Driver does not provide the FireGL X11 extensions! Panel components will operate only partially." the panel then pops up, but there are no things to configure. 



Does anybody know how to help me fix the tearing problem w/ compiz.
I think it has to do w/ vsync and if I could get driconf to work, I think I could fix the tearing.

P.S. I don't know if this is relevant or not, but when I type "glxinfo | grep direct" in the terminal, it says direct rendering = no.

---

