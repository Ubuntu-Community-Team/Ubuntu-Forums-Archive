---
title: "Slow performance in Xubuntus and Lubuntus with games."
date: 2012-11-30
forum: Desktop Environments
---

### Post by Portaro on 2012-11-30
I find the solution to pcs with ATI graphic cards and Xubuntu or lubuntus installed.

I have this problem in last months on my xubuntu remaster 12.04  [http://tux-a-solta.blogspot.pt/p/tas.html](http://tux-a-solta.blogspot.pt/p/tas.html) .

I try many tricks like edit xorg, remove xserver ati, edit the programs that start automatically with boot, install xorg-edgers, etc etc.

I dont remind all tricks i do.

I test many distros to try to find solution, i have 2 pcs with XUbuntu and the problem is the same -  in the desktop pc i have an ATI 9250 with an Intel processor 1.5GB RAM, and i also have a laptop with an ATI 2400 HD with an Itel processor also with 2GB RAM.

The problem in two pcs is same slow games performance, compiz dont work, and the graphic cpu show an excessive charge of use.

I can obtain an result with command glxgears and the 3d image works but games no, but when i open glxinfo there is no result, so i investigate if the problem  if DRI or mesa have any problem and i see that mesa-utils is not installed on the LXDE and Xfce desks.

This affect the systems i think the Ati cards dont work well without this pack config for mesa.

In past i thinking if problem is poor hardware for new kernels, or if i need come back to older Ubuntus.
But the problem solved with install mesa-utils, so   after install this package the games on both pcs works  the compiz works well, games like 0AD, torcs, Stunrally works, warzone2100 etc, the charge of cpu is much more stable and short, my desk pc coolers are much more stables.

Maybe other users with ATI and Xubuntu Lubuntu have this problem and after months i have the answer.

---

### Post by amethyst igor on 2012-11-30
I think that is because mesa-utils installs OpenGL support, which is hardware acceleration used by your games and by compiz.

I installed a proprietary hardware acceleration, ATI's fglrx and libva, to get similar results.

---

### Post by TenPlus1 on 2012-12-01
You SHOULD be seeing better results when running 3D games on X/Lubuntu since they are not as visually intensive as Ubuntu's Unity...  Have you tried Kubuntu, it has a special feature that disables certain things during full screen playback and gaming that makes games even faster than normal...

---

### Post by Portaro on 2012-12-01
Today i Experiement the laptop battery mode, but the pc also stop in periods, this stopeds is not present then past without mesa-utils but still works bad only on batery mode if i use electric power the pc go well.

What can i do?

Maybe go to Kubuntu but i prefer Xfce to KDE and i dont like unity or gnome3.

MAybe i use KDE on laptop if i not find the solution to this new problem.

---

