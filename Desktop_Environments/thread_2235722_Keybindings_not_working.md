---
title: "Keybindings not working"
date: 2014-07-22
forum: Desktop Environments
---

### Post by PenguinLust on 2014-07-22
I went to the keyboard preferences and the "Shortcuts" tab and under custom, I had it execute "gedit" and bound it to Ctrl+Alt+N. Well, Ctrl+Alt+N doesn't do anything. It's not being absorbed by any particular app, because I can minimize all the other apps and it still doesn't work.
Perhaps I should mention that I had to customize my desktop, because I wanted to have my system buttons on the right instead of the left. So I had to load a legacy-type of desktop for that.

---

### Post by mctiew on 2014-07-22
Did you check the default keyboard short cuts are working ?

Is it only those custom shortcuts are not working while the default ones are still working ?

I have the case of from time to time all the keyboard shortcuts are not working, including the default ones. I am still trying to figure out why.

---

### Post by PenguinLust on 2014-07-30
The default ones seem to work. I managed to launch a terminal and lock the screen.

---

### Post by PenguinLust on 2014-08-07
It just spontaneously started working.
I'm finding some superficial quirks in this version. Another thing that tends to happen is the theme cursors reverting to default (which seems to happen when I start the system w/out an Internet connection)

---

### Post by mctiew on 2014-08-08
> **mctiew said:**
> Did you check the default keyboard short cuts are working ?

Is it only those custom shortcuts are not working while the default ones are still working ?

I have the case of from time to time all the keyboard shortcuts are not working, including the default ones. I am still trying to figure out why.

I continue to experience this.

I still haven't quite figured out how it happened but it could be :-

1. Not working since boot. Maybe some crashes during start-up could have caused this. Unconfirmed and unlikely.

2. Not working after wake up from sleep or change display. Because I seldom reboot my notebook, from time to time I will put the notebook to suspend/sleep and then switch the display at office external display and at home internal display. One of these could have cause the problem. Again unconfirmed but quite likely

I wonder if they is anyway to troubleshoot the problem ? What scripts to look into ? Log files ? Which program is responsible or handling keybinding and shortcuts ? Xorg or what ?

---

