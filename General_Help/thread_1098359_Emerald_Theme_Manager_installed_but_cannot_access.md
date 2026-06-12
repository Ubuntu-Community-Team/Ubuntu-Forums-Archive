---
title: "Emerald Theme Manager installed but cannot access"
date: 2009-03-16
forum: General Help
---

### Post by AeroNautica0909 on 2009-03-16
Hey everyone!

I'm having this problem. I had to reinstall Ubuntu Intrepid on my Thinkpad T61p laptop. I have Compiz installed and functioning. However, I want to install Emerald and use it as my window decorator. The problem I'm having is I installed it using Synaptic but it does not show under the Preferences menu. It used to show before I had to reinstall Ubuntu on my laptop.

Can someone outline the exact process on how to install it or what to do so I can set Emerald as my window decorator? Thanks!

---

### Post by Partyboi2 on 2009-03-18
If its not showing up under System>Pref check Main menu (System>Pref>Main Menu) that is has a tick next to it.

You can also start if from the terminal with
```
emerald-theme-manager
```

---

### Post by ruel- on 2009-03-18
```
emerald --replace
```
:)

---

### Post by AeroNautica0909 on 2009-04-02
Thanks for the info! I figured it out. I had a KDE 3.5 repository (Pearson Repository) that had its own Emerald Theme Manager which conflicted with the official repository. I disabled that repository so I can get the official Emerald Theme Manager installed.

---

