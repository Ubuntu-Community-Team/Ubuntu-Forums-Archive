---
title: "Ubuntu MID: Turning off maximizing?"
date: 2009-06-03
forum: Desktop Environments
---

### Post by tannalv on 2009-06-03
Quick question, how do I turn off maximizing feature? A lot of things don't work bc of it.
Thank you.

---

### Post by pauna on 2009-06-03
> **tannalv said:**
> Quick question, how do I turn off maximizing feature? A lot of things don't work bc of it.
Thank you.

You have a background process called *maximus* running, which automatically maximizes everything.

You can remove the maximus process from the automatic startup sequence (System -> Preferences -> Startup Applications in normal Gnome GUI, I don't remember how it goes in netbook remix) and the normal behaviour should come back.

If you don't want to get rid of it totally, you can use gconf-editor to manipulate maximus' configuration (/apps/maximus) to exclude certain application classes from the maximization. However, getting things right piece by piece is not very easy.

---

### Post by tannalv on 2009-06-03
Thank you very much. :-)

---

