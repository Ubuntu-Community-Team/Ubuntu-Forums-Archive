---
title: "TwinView with Different Monitor Sizes"
date: 2005-06-06
forum: Desktop Environments
---

### Post by Cmdr_K00n on 2005-06-06
Hey all,

I have a spare 15" LCD sitting around at home.
I want to have both my 17" LCD (DVI) and my 15" LCD (RGB) running.

I have heard that I may have to mess around with modelines and the such, and I have not the faintest idea about all of it. Also I gather that I would have to run Both of my monitors off the rgb connections if I was to do this, and both of them at the lower 1024x768 res that the 15" supports and not the full 1280x1024 that my 17" suppoprts.

Has anyone had any experience with this?

---

### Post by jimboberella on 2005-07-20
I've just finished playing with this using nvidia's twinview and I could not get it to work.

I was trying the same thing 17" DFP + 15" DFP

It appears both monitors are assumed to be capable of the same resolutions or you get the lowest common denominator. remember that twinview attempts to assign one big desktop so the resolution has to be one that wills span both monitors and still fit inside the abilities of the smallest one. I ended up  with 720x480 on the 15" and 1024x480 on the 17"

You can do it so that each screen is a seperate X root screen but then you can't drap between screens etc.

I'm reading about Xinerama now but I think it will want the screens to be the same size too.

---

