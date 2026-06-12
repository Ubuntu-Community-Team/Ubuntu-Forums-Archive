---
title: "Help with key shortcuts"
date: 2009-04-28
forum: General Help
---

### Post by soskito on 2009-04-28
I have installed xubuntu 9.04 3 days ago, and now (because before they did) the Ctrl+Alt+Delete, Ctrl+Alt+Backspace or Alt+F2 shortcut arent working.   Curiously, Control+Alt+d work.  There is no problem with the configuration of shortcuts. I can run xfrun4 and xflock4 from terminal, but I want the shortcuts to work again.  Any idea?

---

### Post by sisco311 on 2009-04-28
Go to Menu -> Settings -> Xfce4 Settings Manager -> Keyboard > Application Shortcuts tab and add the shortcuts or reset them to default.

---

### Post by soskito on 2009-04-28
they were already on default, the problem stills the same

---

### Post by soskito on 2009-04-28
> **sisco311 said:**
> Go to Menu -> Settings -> Xfce4 Settings Manager -> Keyboard > Application Shortcuts tab and add the shortcuts or reset them to default.

none of those shortcuts work,  maybe they arent being triggered? i cannot take screenshots either..

---

### Post by soskito on 2009-04-28
any idea?

---

### Post by shawnrgr on 2009-04-29
Im having a similar issue on ubuntu 9.04. default settings for 'Log Out' say c+a+del. However it gives me the shutdown dialog with no log out option. Alt+F2 for run dialog isn't working at all.

---

### Post by soskito on 2009-04-29
bump

---

### Post by dgraham on 2009-06-25
I had the same problem today, and fixed it by logging in on a console and deleting ~/.cache/sessions and ~/.cache/xfce4 (not sure which one was the problem). This is one of my first troubleshooting steps anymore, as sessions have been pretty iffy over the last two releases. ](*,)

---

### Post by orengolan on 2010-05-22
i have the same issue on karmic.
I tried dgraham's solution but it didn't work for me. any other solutions?

---

