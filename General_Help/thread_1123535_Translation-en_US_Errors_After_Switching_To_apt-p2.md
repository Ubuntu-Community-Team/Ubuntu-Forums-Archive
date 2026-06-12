---
title: "Translation-en_US Errors After Switching To apt-p2p"
date: 2009-04-12
forum: General Help
---

### Post by BrainwreckedTech on 2009-04-12
OK, I *think* I'm getting the gist of what's going on.  Or I could be completely wrong.  Either way I have no idea where to start.

When I used regular ol' apt, I had no errors whatsoever.  When I started using apt-p2p, I started seeing Ign in the terminal and Failed in the Update Manager.  The failures always correspond to attempts at retrieving Translation-en_US.

My guess is that under apt, there was some communication somewhere that I was using an en_US system and Canonical's servers where able to tell my system that they were en_US.  Or maybe there's a setting on my system somewhere telling my system that archive.ubuntu.com, us.archive.ubuntu.com, and security.ubuntu.com are en_US servers.

Anyway, it seems that's "broken" now with apt-p2p.*  I think it has to do with the apt not knowing the native language of localhost.  Since it doesn't know, it errs in safety and tries to get Translation-en_US.  As I'm mirroring en_US servers, Translation-en_US isn't going to exist.  So apt follows the Linux mantra of fully letting the user shoot himself in the foot.  (If they were not en* servers I'd be screwed.)

Any clues as to what's going on and how to fix it?

*By "broken" I mean "driving me nuts with error message that ultimately have no effect on usefulness or end result I just like avoiding error message when I can because the less useless error messages there are the easier it is to find the ones that matter.

---

