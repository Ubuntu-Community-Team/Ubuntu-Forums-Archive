---
title: "middle click paste"
date: 2014-11-07
forum: Desktop Environments
---

### Post by cmcanulty on 2014-11-07
My middle click paste that I love stopped working, how do I fix it? I am running xubuntu14.04 64bit.

---

### Post by ajgreeny on 2014-11-07
Has it just stopped working, or did this happen after an update from a previous Xubuntu version?

Middle click to paste is working fine here.

---

### Post by Impavidus on 2014-11-07
Are other middle click functions still working? Just to rule out a broken mouse button.

---

### Post by cmcanulty on 2014-11-07
yes it scrolls OK  it just stopped pasting yesterday and I love that function especially for the terminal

---

### Post by ajgreeny on 2014-11-08
How about a middle-click on a link to open a new tab in Firefox or Chromium?  Does that work?

---

### Post by Impavidus on 2014-11-08
If you open up a mouse you can see that the middle click with the mouse wheel works by the entire wheel mounting pushing on a simple push button, whereas scrolling works using a light sensor in the wheel mounting counting the spokes of the wheel. So the clicking and scrolling actions are unrelated.

---

### Post by OidaWappler on 2014-11-08
You can use xev to monitor mouse events: (event mouse works as a filter)

[FONT=courier new]xev -event mouse[/FONT]

Something like that should show in the terminal while hitting the middle button (=button 2) whereas scrolling is Button 4 and 5 ! As previously noted it is not the same switch at all.

ButtonRelease event, serial 25, synthetic NO, window 0x4600001,
    root 0x2c6, subw 0x0, time 21531884, (83,120), root:(634,714),
    state 0x210, button 2, same_screen YES

Just to see if it is driver/hardware related or a config issue ...

---

### Post by cmcanulty on 2014-11-08
weird I put that in terminal and all the sudden it works again, thanks

---

