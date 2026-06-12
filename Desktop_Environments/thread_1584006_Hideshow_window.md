---
title: "Hide/show window"
date: 2010-09-28
forum: Desktop Environments
---

### Post by mrs.tort on 2010-09-28
As a gnome completely hide the window using a console command? It is necessary that the windows would have been in the window list and it is not hidden in the tray.

---

### Post by mrs.tort on 2010-09-29
Up

---

### Post by ankspo71 on 2010-09-29
Hi,
I didn't understand the question, so I will ask this...
Are you looking for a way to hide applications in the system tray?

Install "alltray" and give that a try. You can run alltray by itself in the system tray so you have quick access to hide any window you like. Or you can change your start menu entries so that the applications automatically go to the system tray every time, like this:

Example for Firefox:
alltray firefox

---

### Post by mrs.tort on 2010-09-29
No, it's not what I need.

---

### Post by Frogs Hair on 2010-09-29
Check the Opacify box in Compiz and this allows you to hide a window by hovering the  arrow  over the window you would like to view . Make sure normal desktop effects are enabled.

---

### Post by mrs.tort on 2010-10-29
anyone have any ideas?

---

### Post by jbruced on 2010-10-29
yes. my idea is to explain what you are trying to accomplish. i can't understand what you are trying to do.

---

### Post by mrs.tort on 2010-10-30
I need to achieve the same result as the use of "alltray", but not using this program.

---

### Post by mrs.tort on 2010-11-02
Get window ID:
```
wmctrl -l
```

Hide window:
```
xdotool windowunmap ID
```

Show window:
```
xdotool windowmap ID
```

---

