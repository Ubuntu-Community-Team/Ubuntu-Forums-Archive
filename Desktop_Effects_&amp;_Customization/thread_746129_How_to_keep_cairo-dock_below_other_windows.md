---
title: "How to keep cairo-dock below other windows?"
date: 2008-04-05
forum: Desktop Effects &amp; Customization
---

### Post by Malfet on 2008-04-05
In default mode Cairo-Dock is always above of other windows, what is not really convinient for a small laptop screen. I've tried to put it below by Compiz Window rules, but did not succeed with different window name variants.
Does anybody know how to define a proper window name for compiz settings? If that suppose to work with docks as well.

Thanks,
M.

---

### Post by vmalep on 2008-05-03
Hi,

This is funny: I am trying to achieve exactly the opposite! And I am facing similar problems. You can check this thread [How to keep cairo-dock of the panel]("http://ubuntuforums.org/showthread.php?t=777673&highlight=cairo-dock").

Actually, the "Above" field had been working for some times, but had to be modified after every boot. Then it stopped working after I had installed additional plugins as explained in this thread: [Compiz-Fusion, la fusion de Beryl et de Compiz]("http://doc.ubuntu-fr.org/compiz_fusion#utilisation") (in French). Since then, it seems that the window-rules module does not work. I unchecked several plugins and removed emerald, but it did not help...

---

### Post by smidgey on 2008-05-24
G'day, I've just moved to cairo-dock and I was having the same drama, so I submitted a patch to add this feature. If you are a brave soul (it's heavily untested) you could checkout the latest source from svn, then apply the [patch]("http://developer.berlios.de/patch/index.php?func=detailpatch&patch_id=2476&group_id=8724").

A compile & install later, and you should be rockin' out.

[This thread]("http://ubuntuforums.org/showthread.php?t=613087") has a description of a quick way to get the source and all the dependencies that you need.

---

### Post by linuxsamurai on 2008-05-30
Hey guys i also had such problems for a while now and just literally figured out a way to get around this.

If you have Beryl installed there is an option in the Beryl Settings Manager in the Desktop Section called Widget Layer.

Basically if you click the + sign on the right and write cairo-clock it makes the dock a widget. (Don't forget to tick the Widget Layer Box)

It makes the Dock as a widget and therefore hides it under windows.

How that was of some help

Glad to help

--Will--

---

