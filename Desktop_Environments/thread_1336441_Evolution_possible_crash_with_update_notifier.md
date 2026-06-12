---
title: "Evolution: possible crash with update notifier?"
date: 2009-11-24
forum: Desktop Environments
---

### Post by pataphysicianu on 2009-11-24
This has only happened to me twice so far, so I'm not sure what is the cause, but there is a suspicious correlation.

I'm running evolution with standard notification with the new notification applet, I have evolution set to play a sound, notify in panel and display notification message. These all work fine for me. I leave evolution opened and minimized.

Twice evolution was totally locked up, though it still appeared to be running in in it's minimized state, the first time I had to kill it, as no Force quit dialog ever came up. The second time I could use the force quit to get out. 

The interesting thing is this happened after I changed the configuration of the update-notifier in gconf to notify me of recommended updates everyday(instead of every 7 days). And in both cases the update app was up automatically because of new updates.

The problem doesn't seem to happen from just opening update manager, but seems triggered by update-notifier automatically loading update manager. Also the first time it happened, the new notification mail applet when clicked would quickly show it's menu which would then disappear.

I was wondering if anyone else has seen this problem?

---

