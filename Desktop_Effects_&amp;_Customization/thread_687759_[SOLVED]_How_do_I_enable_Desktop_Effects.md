---
title: "[SOLVED] How do I enable Desktop Effects?"
date: 2008-02-04
forum: Desktop Effects &amp; Customization
---

### Post by toastysquirrel on 2008-02-04
Technically I know how to *enable* them, it's just not working.  I'm running Gutsy with an ATI X700 video card with Restricted Drivers enabled, I also have xserver-xgl installed (though it's disabled).  Whenever I try to enable desktop effects, I receive the error message "Desktop effects could not be enabled".

The only way I've gotten them to work so far has been to disable the restricted driver (fglrx) and re-enable xserver-xgl; but doing so causes my system to run REALLY slow due to rendering issues.  Even opening folders and moving windows becomes painfully slow.

How can I enable desktop effects (because I also want to be able to run AWN) without causing my system's ability to render *anything* to grind to a halt?

Thanks guys!

Oh yeah, and I'm really new at all this too :)

---

### Post by zarqoon on 2008-02-04
Try enabling xgl with the ati driver enabled. Worked for me

---

### Post by toastysquirrel on 2008-02-04
> **zarqoon said:**
> Try enabling xgl with the ati driver enabled. Worked for me
I swear I thought I had tried that before.  Sure enough, it seems to work fine.  Freakin' weird dude, but hey, no arguments coming from me.  Thanks Zarqoon!

---

