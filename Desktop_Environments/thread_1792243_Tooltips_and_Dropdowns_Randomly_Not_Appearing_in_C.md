---
title: "Tooltips and Dropdowns Randomly Not Appearing in Compiz"
date: 2011-06-28
forum: Desktop Environments
---

### Post by Joseph Schwenker on 2011-06-28
I've been having an issue for the past several months where, when Compiz is enabled, items with tooltips will not show the tooltip when hovered over until I move the mouse slightly. To see a demonstration of this, go [here]("http://www.youtube.com/watch?v=sbObRdHfgME"). Note that this does not happen when Metacity is enabled instead of Compiz.
The other part of this issue is that some dropdown menu items will not appear until I mouse over them, similarly to the problem with tooltips. You can see a brief demonstration of that in the final few seconds of the first video, but it can be seen in more detail [here]("http://www.youtube.com/watch?v=TkXUrWKLoqY"). Despite the title, the problem appears in both Wine and native applications. Similarly to the first problem, this issue does not occur when Metacity is enabled in place of Compiz.
Can anyone help me solve this?

---

### Post by Joseph Schwenker on 2011-07-06
bump

---

### Post by Joseph Schwenker on 2011-07-11
bump

---

### Post by Joseph Schwenker on 2011-07-24
bump

---

### Post by eeg on 2011-10-23
This is months late but just in case you're still having the problem (or google brings someone else to this thread).

Had the exact same problem. But I'm in Archlinux using latest gnome-3 and compiz.


After hours trying to solve it, the solution was simple: just enable animations in compiz (the plugin that allows you to animate windows when they appear or close) [ccsm->Effects->Animations]


Not sure it's an entirely compiz issue. Problem exists in all gtk apps (except Firefox, which has XUL between it and gtk).

---

### Post by Joseph Schwenker on 2011-10-23
The problem didn't just affect GTK applications for me. Wine applications were also affected, as seen here: [http://www.youtube.com/watch?v=TkXUrWKLoqY](http://www.youtube.com/watch?v=TkXUrWKLoqY)

---

### Post by eeg on 2011-10-23
Don't run WINE so I can't comment.

Just tried with Qt-creator (which runs atop QT) and I had the same issue, so its probably just compiz's way of handling tooltips/dropdownmenus.

Firefox is the only application where the problem doesn't exist.


In any case, turning on animations solved it for me. Did it work for you?

---

### Post by Joseph Schwenker on 2011-10-24
Actually, I haven't had the problem since I did a clean installation of Ubuntu 11.04, so I can't say whether it works or not. Hopefully your solution will help someone else who encounters the problem.

---

