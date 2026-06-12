---
title: "Failing to spawn gnome-panel in Jaunty NBR"
date: 2009-04-28
forum: Desktop Environments
---

### Post by donaldGuy on 2009-04-28
Hello,

I installed Jaunty Netbook Remix on my Eee PC 901 the other day and its been mostly working fine. Today, however, when I booted it, it spawned the nerbook-launcher but failed to spawn the corresponding gnome-panel (or possibly the whole gdm, since windows didn't have window decorations either). When I ran gnome-panel manually, it showed up in the right place but no processes that I opened thereafter would work on it.

I have a workaround: running desktop-switcher and switching to "Classic mode" and back again is enough for everything to get set up right.

Its been awhile since I've used a proper linux distro, so I'm a bit hazy on the proper debugging procedure. I can't find any errors about why its not spawning in /var/log, but maybe I'm just not looking in the right place.

In any case, any debugging advice would be helpful.
~Donald

P.S. Is this worth filing a bug over? It is reproducible on my machine.... but I don't really know what information about my configuration is relevant without really tracking down the problem myself.

---

