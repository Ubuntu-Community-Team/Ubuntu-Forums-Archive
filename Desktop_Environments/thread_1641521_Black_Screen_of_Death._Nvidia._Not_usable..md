---
title: "Black Screen of Death. Nvidia. Not usable."
date: 2010-12-09
forum: Desktop Environments
---

### Post by rafrosty on 2010-12-09
Dell Dimension 8200
nVidia geforce2 m/mx 400
Meerkat latest updates, kernel etc

Firefox lagged. I chose not to change pipelining or cache size. Users suggested I update video card. It ran correctly on 10.04, so I thought nothing of it.

I installed it via sudo apt-get install nvidia-current
I restarted
I ran sudo nvidia-config or whatever, restarted
got a black screen with a log in prompt i cannot pass.

This was exactly as per instructions. I hence found additional instructions and am rather angry these people think they know what they are doing, but instead they assume their own indtructions work and do not errata them when this happens.

How can you expect people to appreciate your fine work if a legacy driver like this breaks/disables computers and people know that it disables/breaks computers and have no obvious [COLOR=Red]red alert[/COLOR] status and a wiki page detailing a fix even my father whom knows very little about computers, save XP, (your primary target audience for mainstream acceptance) can run and save his sanity and sleep (never mind my own).

nVidia is now equal to linksys as to something not to purchase again. This driver was updated post meerkat, they should have been working with you (developers).

**It does not work for 10.10 and it needs to be removed from the repository before more are affected.**

Thank you.

---

