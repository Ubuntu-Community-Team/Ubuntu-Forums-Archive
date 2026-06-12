---
title: "Uninstallation of linux-generic, linux-headers-generic, etc..."
date: 2009-06-05
forum: General Help
---

### Post by jaminthorns on 2009-06-05
I just reinstalled Ubuntu on my Aspire One and everything went fine until I noticed that (after installing all the upgrades) the packages linux-generic, linux-headers-generic, linux-restricted-modules-generic, and linux-image-generic couldn't be updated. I tried to update them with both Synaptic and apt-get but neither worked. Eventually, I just got annoyed with them staying in my update manager window, I just removed them with Synaptic. I quess this was kind of stupid but no damage has been done whatsoever. If i do need them, I can still install them if I disable jaunty-proposed updates and install an older version. So I'm just wondering, do these packages provide upgrades for your kernel or are they just useless?

---

### Post by LepeKaname on 2009-06-06
They are not useless... They exist to provide more stability to your settings. You may not need them until you have to update your kernel. Then I recommend you to have those packages there. They are kind of aliases, with them you are ensured that you have the last kernel version updated. 
I recommend you to use aptitude instead of synaptic or apt-get. It is the best resolving packages conflicts. It is not as easy as synaptic but it is not that hard. Run it without arguments and you will see the UI.

---

### Post by randiroo76073 on 2009-06-06
Even tho it shows up in synaptic(also apt-get,aptitude), linux-generic 2.6.28.13.17 doesn't seem to be available yet

---

### Post by n0_mad on 2009-06-06
I get this problem too. So is problem with repos or we should manually fix dependencies?

---

### Post by DizzyTech on 2009-06-06
It seems that somebody screwed up the uploading of the new *actual* kernel packages to the server/mirrors.  The 2.6.28-13-generic packages (and their -virtual, -386 friends as well) simply don't exist on the Proposed repo, neither on the main Ubuntu repo server or the United States one (and, certainly no mirrors).

---

### Post by fendora on 2009-06-07
anyone have solution for this problem ? im having the same prob ...

---

### Post by n0_mad on 2009-06-09
bump

---

