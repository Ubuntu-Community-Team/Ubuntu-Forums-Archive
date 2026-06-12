---
title: "KDE / Update Manager problems?"
date: 2009-03-27
forum: General Help
---

### Post by iheartubuntu on 2009-03-27
Some time back I had added KDE to my computer so I could do such programs as KTouch, Marble, etc. Within the last month Ive noticed I am having update problems in Update Manager. It asks me to do a partial upgrade. When I click OK, the Update Manager disappears and never comes back up. And pretty much nothing else happens after that point unless I go back into Update Manager myself.

My problems may have begun when I got tired of nightly upgrades to KDE of 150mb each. No big deal here at home as I have really fast speeds, but at work (where I also have the same prob! Ugggh) I removed those nightly upgrades in the Software Sources (third party software PPA's).

So, Im at this point where I try to install suggested updates, but it now prompts me for "partial upgrade" in the Update Manager. I have to select "close" instead of doing the partial update, then do the few new updates I can, but I have a long, greyed-out list of KDE updates that never update.

Any way to fix my system and get me back on track? Much appreciated if you can help! Thanks.

---

### Post by Xiong Chiamiov on 2009-03-27
```

sudo apt-get update && sudo apt-get upgrade

```
should update you.  Report back if you have any problems.

---

