---
title: "Help with logout dialog"
date: 2009-05-10
forum: Desktop Environments
---

### Post by vvd416 on 2009-05-10
Does anybody know how to configure buttons in the logout dialog in Xubuntu 9.04?
What I want is to remove the Suspend and Hibernate buttons since my hardware doesn't support these functions. I played with gconf-editor, but gnome-power-manager settings seem to have no effect on that dialog.
Any help will be appreciated.

---

### Post by ckonestroh on 2009-05-11
> **vvd416 said:**
> Does anybody know how to configure buttons in the logout dialog in Xubuntu 9.04?
What I want is to remove the Suspend and Hibernate buttons since my hardware doesn't support these functions. I played with gconf-editor, but gnome-power-manager settings seem to have no effect on that dialog.
Any help will be appreciated.

Easy restart computer or logout should remove from menu

---

### Post by vvd416 on 2009-05-11
I'm not sure that I understand you.
Could you explain your idea, pls?

---

### Post by vvd416 on 2009-05-12
I found the solution, it's given here:
[http://support.zenwalk.org/viewtopic.php?f=10&t=21764]("http://support.zenwalk.org/viewtopic.php?f=10&t=21764")

For those who are not interested in the whole thread - run

xfconf-query -c xfce4-session -np '/shutdown/ShowHibernate' -t 'bool' -s 'false'
xfconf-query -c xfce4-session -np '/shutdown/ShowSuspend' -t 'bool' -s 'false'

---

