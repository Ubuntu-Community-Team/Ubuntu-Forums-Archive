---
title: "Kubuntu &quot;gutsy&quot; 7.10 beryl = no window borders"
date: 2007-06-13
forum: Desktop Effects &amp; Customization
---

### Post by pony-tail on 2007-06-13
I have just installed Kubuntu 7.10 "tribe 1" clean install.
I installed the repo version of beryl .
The cube functions perfectly but I have no borders and can not resize or move windows .
Hardware is Shuttle SB61 g2 (Intel 865 chipset) GF 6800 gt video card , 1 gig ram .
I am running nVidia binary drivers .
Anyone got any ideas ?
I have Googled and found nothing of use as well as searching ,Ubuntu , Kubuntu and Beryl forums and found very little of use .

---

### Post by pony-tail on 2007-06-13
Worked it out
A combination of two fixes worked for me.
First code : sudo nvidia-xconfig --add-argb-glx-visuals -d 24
Second , In Beryl-manager set it to "force aiglx" under "rendering platform"

---

### Post by Balistic on 2007-06-13
How did you get beryl to work under KDE in the first place?  My system runs Beryl perfectly when I use Gnome, but when I open beryl-manager under KDE nothing happens..

---

### Post by rich.bradshaw on 2007-06-13
aquamarine is the decorator, not emerald. That's often the problem for people used to Gnome.

---

### Post by Nythain on 2007-06-13
i ran beryl/emerald under kde no problems

---

### Post by Balistic on 2007-06-13
> **rich.bradshaw said:**
> aquamarine is the decorator, not emerald. That's often the problem for people used to Gnome.

OK, but how do I run it...???

---

