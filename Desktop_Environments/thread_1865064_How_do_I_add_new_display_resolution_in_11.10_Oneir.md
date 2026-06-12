---
title: "How do I add new display resolution in 11.10 Oneiric Ocelot?"
date: 2011-10-19
forum: Desktop Environments
---

### Post by TAStott on 2011-10-19
Hello,

I'm looking for a way to permanently add a new display resolution for an additional monitor in Ubuntu 11.10.

In 11.04, I edited */etc/init/gdm/Default *as advised [here]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html") and that worked perfectly. However, although I kept the edited file when I upgraded, it no longer has the desired effect.

Serves me right for upgrading straight away even though I'm an Ubuntu noob!

Any help much appreciated.

Tim

---

### Post by fantab on 2011-10-21
> **TAStott said:**
> Hello,

I'm looking for a way to permanently add a new display resolution for an additional monitor in Ubuntu 11.10.

In 11.04, I edited */etc/init/gdm/Default *as advised [here]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html") and that worked perfectly. However, although I kept the edited file when I upgraded, it no longer has the desired effect.

Serves me right for upgrading straight away even though I'm an Ubuntu noob!

Any help much appreciated.

Tim

Oneiric Ocelot **does not use gdm** anymore it has moved to **lightdm**, so maybe we have to edit /etc/init/lightdm.conf to make this forced monitor resolution workaround permanent. How? I don't know yet. 

I hope someone figures it out... because I too will need this solution once I install Oneiric to my older desktop which has always had this is issue.

---

