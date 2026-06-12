---
title: "Monitor woes (can't increase resolution)"
date: 2009-05-07
forum: General Help
---

### Post by jimsteele on 2009-05-07
Hello,

I've recently installed Ubuntu Studio (9.04) and I'm having a terrible time getting my monitors set up correctly.

I have 2 screens, one smaller than the other, which I use in XP as a dual screen configuration with no problems. The main screen runs @ 1280x1024, the smaller one @ 1024x768. I'd like to replicate this set up in Ubuntu, unfortunately it refuses to output to the main screen at anything higher than 1152x864, which looks pretty rubbish.

I've tried to solve this problem myself, googling like crazy and making loads of xorg.conf edits, most of which seem to either be ignored or screw the system. I'm coming to the end of my tether with it really, but I really don't want to go back to windows full time. If anyone can help me out I'd be eternally grateful!

GFX card: Nvidia 8600gt (running latest proprietary drivers)
Monitors: Iiyama Vision Master 505 (comes up as "unknown CRT"), LG 15" lcd (which is detected perfectly)

All I want to do is run the main screen at 1280x1024. Are there monitor drivers I can try? I'm guessing the fact that the Iiyama isn't being detected correctly may be the root of my problem here.

Thanks,
Jim

---

### Post by wabbalee on 2009-05-07
I would say so too, with regards that your monitor is not detected properly. This is not going to help you but there is something different in Jaunty compared to Hardy when it comes to installing monitors; your question made me check in system settings on how to set the monitor manually but the option of doing this seems absent, unlike Hardy where one could pick the brand and type of monitor from a list, which was a darn good feature.

does anyone know of this feature in Jaunty, or how to get it?

---

### Post by jimsteele on 2009-05-07
Hmm, thanks for pointing me in another direction! I've done a bit of googling on that score, wondering if there's a package I can install that'll give me the option you suggest on Jaunty.

Is there any option (in xorg.conf or otherwise) to simply force the machine to output 1280x1024?

---

