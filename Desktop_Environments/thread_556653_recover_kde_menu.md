---
title: "recover kde menu?"
date: 2007-09-21
forum: Desktop Environments
---

### Post by roar on 2007-09-21
I installed sabayon alongside kubuntu and had them share /home. problem is this messed up the botom menu in kde and all the icons for stuff like system updates, network connection are gone. also, ktorrent doesnt display, as the icon for it also used to be in that menu.

Is there some way I can recover the menu from original kubuntu ?

---

### Post by kellemes on 2007-09-21
Don't know..
I do know you better not share /home partitions, you always have to deal with version differences of packages, and so user-configuration-settings will differ.

---

### Post by roar on 2007-09-22
yes, because sharing home doesnt seem to be well supported, I agree. still I find in many situasiotn it is advantageous to share it.

anyways , fixed it by moving ~/.kde/share/apps/kicker and ~/.kde/share/config/kickerrc

---

