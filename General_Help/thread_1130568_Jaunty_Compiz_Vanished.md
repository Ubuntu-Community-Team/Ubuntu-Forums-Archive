---
title: "Jaunty Compiz Vanished"
date: 2009-04-19
forum: General Help
---

### Post by Venko on 2009-04-19
Hey, I'm using the release candidate of Jaunty on my Inspiron 1525. There's an existing problem with Intel graphics that means really poor performance but up until today my Compiz at least worked. That's no longer the case.

When I go to Appearance and try to enable Compiz I get "Searching for drivers..." and then eventually "Desktop effects could not be enabled". I tried asking in #ubuntu+1 and was pointed in the direction of [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392?comments=all").

I don't know how this is the cause of my Compiz problem as it worked fine until today but I tried installing the mesa versions linked to in Andres Mujica's comment. No difference.

How can I go about getting Compiz back? I'm currently considering reverting to Intrepid and skipping the Jaunty release all together as the the poor Intel graphics support and now lack of Compiz are making me consider whether a new version of GNOME and a new notification system are worth it.

**[edit]** Seems this will start Compiz for anyone else experiencing the problem: SKIP_CHECKS=yes compiz

**[edit]** This fixes the speed of the graphical performance too (I installed the old mesa packages and Intel driver 2.4) so Jaunty isn't seeming so bad after all.

---

