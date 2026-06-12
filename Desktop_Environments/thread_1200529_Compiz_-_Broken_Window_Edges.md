---
title: "Compiz - Broken Window Edges"
date: 2009-06-30
forum: Desktop Environments
---

### Post by siabost on 2009-06-30
Hi,

New Desktop: Ubuntu & Kubuntu 9.04, AMD 64 Athlon 2.7Ghz, Integrated nVidia Graphics with Ubuntu-recommended V180... proprietary driver.

On Gnome desktop with Compiz activated, to get Spinning Cube & wobbly windows effect (Gnome Compatibility is ticked),I get a broken edges effect when dragging windows about the desktop.

If I log out & switch to the KDE4 desktop everything is fine & the wobbly windows effect works smoothly with good clean window edges as I drag things around!

When in Gnome I've tried enabling/disabling things in Compiz & reducing the effects to the "second level" on the Visual Effects tab but the broken edges are still there.

I always thought the KDE4 desktop was a heavier ask for the graphics than the Gnome desktop, so load on the graphics card shouldn't be the reason.

Does anyone have any ideas as to why the problem exists in Gnome but not in KDE4? And any solutions?

Thanks.

---

### Post by voncarlsson on 2009-06-30
Vertical sync?

---

### Post by drs305 on 2009-06-30
> **siabost said:**
> Does anyone have any ideas as to why the problem exists in Gnome but not in KDE4? And any solutions?

Thanks.

Check the CompizConfig Configuration Manager (System, Preferences, CommpizConfig...) "Windows Decorations", Command. Is it using the compiz decorator or the gtk-windows-decorator? If the former, try changing this entry to "gtk-window-decorator --replace". If the latter, this should not matter but try changing it back to the default "/usr/bin/compiz-decorator".

Note: You can easily switch to the GTK decorator if you install "fusion-icon".

---

### Post by siabost on 2009-07-03
Hi,

I've just realised that KDE4 (Kubuntu)'s effects are built in to KDE4 and (I think) not produced/controlled by Compiz, so that may explain the difference between the two.

How do I set the Vertical Sync? Nothing quite seems to match in "nVidia Settings" control.

I will try the "Fusion Icon" route to see if it's the Window Decorator causing the problem.

Thanks

---

### Post by User Abuser on 2010-10-12
I wish someone would post any solution to this  :(
Problem is that I use Firefox and Opera sidebar A LOT and I also middle-click edges to rotate cube. This invisible border is making sidebars practically unusable. When "Rotate Cube" is off edges work fine!

---

