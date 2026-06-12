---
title: "Cant enable desktop effects after update to Lucid Lynx"
date: 2010-05-16
forum: Desktop Environments
---

### Post by willyclaes on 2010-05-16
Everything worked out of the box after an update to Lucid Lynx. I wanted to make the desktop look like the mac so I installed Avant Window Navigator, but that looked like crap.
I couldn't change the themes because I had to enable desktop effects. I checked the box in the appearance menu of the desktop effects without any result. No error message that said "can't enable desktop effects" and also no desktop effects. When I go back to the appearance menu it still have the "no desktop effects" button checked.

I reinstalled compiz without any result. I installed a previous version fro my video card ( Nvidia 9200m GS which is not blacklisted for compiz), without result. I reinstalled the latest driver and now when i start up the top bars of windows are not showing until I try to enable the desktop effects, then they show up, but still no desktop effects.

Any thoughts about this? :(

---

### Post by byStanderone on 2010-05-16
modify xorg.conf, sudo nvidia-xconfig --add-argb-glx-visuals -d 24

---

### Post by willyclaes on 2010-05-16
I entered the code in the terminal and restarted: no result.

I did get an error when I opened the Compiz Manager that another manager might be opened (didn't make screenshot, sorry) or that it interfered with a KDE-program or something like that. I dont have Ubuntu Tweak installed.

Before I updated to 10.04, everything worked. The desktop cube, wobbly effects, everything.

---

### Post by byStanderone on 2010-05-16
...honesty am still confused about this compiz/metacity thing, perhaps its metacity that's in conflict, just a guess, lol.

---

