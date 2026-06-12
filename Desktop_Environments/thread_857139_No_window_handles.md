---
title: "No window handles"
date: 2008-07-12
forum: Desktop Environments
---

### Post by Kraut-striver on 2008-07-12
Hi folks,
I dont get any handles to my windows. I cant move, resize or close them except by clicking the taskbar icons. What can I do about this? Does any one of you know?

---

### Post by coffeecat on 2008-07-12
I'm not quite sure what you mean. If a window is maximised, you cannot resize it even though the 'handles' appear when you hover the mouse near the edge.

If you unmaximise a window, the mouse pointer should change to something like a handle (is this what you mean?) when it is over a horizontal or vertical edge. Or, bottom right, there is a small triangular area which lets you resize in 2 dimensions simultaneously.

If this isn't what you mean and you can't resize unmaximised windows, have you changed any settings in the gconf editor?

---

### Post by Vadi on 2008-07-12
> **Kraut-striver said:**
> Hi folks,
I dont get any handles to my windows. I cant move, resize or close them except by clicking the taskbar icons. What can I do about this? Does any one of you know?

Press Alt+F2 and do "gtk-window-decorator --replace". If that doesn't help, try "metacity --replace".

Edit: By the way, you can close a window by pressing Alt+F4, and move it by holding down alt and left-clicking.

---

### Post by sayakb on 2008-07-12
Did you change your CCSM settings. Open CCSM, click Preferences and click **Reset to Defaults**.

---

### Post by Kraut-striver on 2008-07-13
Hi everybode,

thanks for the kind advice. By "handles", I meant the windows frame, the bar at top of the window where you grab the window to move it and so.
The problem arose because I chose "visual effects" from the "settings->window appearence" dialogue. After choosing "no effects" the problem disappeared.
Now if you can reproduce the problem, we could continue the discussion, otherwise I simply thank you all again.

If you try to reproduce the problem and if you then loose these handles, press Alt+F2 and type "metacity --replace" to bring them back. You then loose the effects again.

---

### Post by sayakb on 2008-07-13
Are you using (or have you installed) emerald theme manager? In that case, press Alt+F2 and type in **emerald --replace**. Also, did you do **gtk-window-decorator --replace **as Vadi said? What was the effect of that?

---

### Post by Kraut-striver on 2008-07-13
Neither of these two helped. Still no windows handles when choosing any visual effects

---

### Post by sayakb on 2008-07-13
At a terminal, do:
```
sudo apt-get install emerald
emerald --replace &
```

---

### Post by Kraut-striver on 2008-07-13
That's what I did, but it doesn't have any effect. Can you reproduce the effect with your desktop?

---

### Post by Vadi on 2008-07-13
No it works fine here heh. Tried "gtk-window-manager --replace"? What does it say in the terminal?

---

### Post by forger on 2008-07-13
try this:
```
sudo apt-get install --reinstall metacity
gconftool -s -t string /desktop/gnome/applications/window_manager/default '/usr/bin/metacity'
gconftool -s -t string /desktop/gnome/applications/window_manager/current '/usr/bin/metacity'
```

log out and log in again.

Are you using ubuntu hardy heron? post the output of this too:
> lsb_release -a

---

