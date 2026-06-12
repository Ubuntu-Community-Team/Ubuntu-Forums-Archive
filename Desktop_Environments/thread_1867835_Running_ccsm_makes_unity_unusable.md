---
title: "Running ccsm makes unity unusable"
date: 2011-10-23
forum: Desktop Environments
---

### Post by JayKav on 2011-10-23
I ram ccsm, just looking at the options. I didn't change any settings even temporarily. It hung when I tried to quit and eventually I had to kill the process. This caused the unity desktop to stop displaying the top menu bar and the icons on the left.

I tried unity --reset. That gave a list of errors and then hung (for 15 mins before I killed it). Most of the errors appeared to be GL-related e.g. "can't bind image to texture". I was able to bring up a terminal using ctrl-alt-t however shutdown hung so I had to do a hard reset. No change after a reboot and I had auto-login enabled so I couldn't turn off unity.

I re-installed (i.e. a repair install) 11.10 which cured the shutdown problem but it made no difference to the desktop. unity --reset returned different errors including one that said "This should never happen, you probably ought to file it as a bug". Unfortunately it didn't say what it was that wasn't supposed to happen. It also hung as before.

I tried a 2nd re-install. Again, no difference. Unity 2D works fine and since it makes remote desktop run considerably faster, I'll probably stay with that anyway but it would be good to know how to repair the damage to unity.

---

