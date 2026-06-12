---
title: "Installing xfce 4.10"
date: 2012-04-29
forum: Desktop Environments
---

### Post by rmcellig on 2012-04-29
I just installed Xubuntu 12.04 and just found out that xfce 4.10 is out now. How do I install xfce 4.10 in my Xubuntu installation? Is it as simple as running a few commands?

---

### Post by 3Miro on 2012-04-29
Xubuntu developers didn't want to risk with xfce 4.10 for the LTS release. In order to get 4.10, you need an unofficial ppa. It should be as simple as a few commands (provided there are no bugs), but couple of Google searches did not return anything.

---

### Post by Toz on 2012-04-29
There currently are no available PPAs. However, you can compile the source yourself. Instructions are here: [http://docs.xfce.org/xfce/building]("http://docs.xfce.org/xfce/building"). 

A couple of issues to be aware of:
1. you need to also build and install thunar-volman
2. you may need to rebuild some of the panel plugins to work with 4.10 (e.g. xfce4-indicator-plugin, xfce4-weather-plugin, xfce4-genmon-plugin, maybe others)

---

