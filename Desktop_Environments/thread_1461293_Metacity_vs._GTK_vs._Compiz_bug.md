---
title: "Metacity vs. GTK vs. Compiz bug?"
date: 2010-04-24
forum: Desktop Environments
---

### Post by ethanmadden on 2010-04-24
Earlier today I upgraded via clean install to 10.04 release candidate, figuring that all of the major bugs would be fixed and planning on just taking the updates that come through for the final release.

The first thing I did was install the Nvidia drivers (and all of those other little things, like restricted extras). I rebooted to finish the Nvidia install, and all was good (surprisingly).

Then I installed compiz. Reboot. It's all good. Then I install compiz config settings manager. Reboot. Everything is good. Then I reset everything in compiz to how I had it on my previous install. Reboot.

This is where it gets weird... For some reason compiz now controlled my window decorations. I opened ccsm and unchecked window decorations, and it rechecked itself. I was like "wtf? this is weird..." so I opened the decoration settings and changed the command to usr/bin/gtk-window-decorations. Reboot to test. 

Now all of my window decorations, menus, and panels were flashing at random intervals. I could see them for just long enough to open a terminal and run metacity --replace. This fixed it temporarily, and I have since restored the compiz settings and set metacity to run at startup instead of GTK. I THINK they were flashing because my system tried to load gtk, failed, and then tried compiz which told it to load gtk, that failed, so it tried compiz... 

Metacity works and is usable, but I wanted Compiz. I also wanted to keep the system window decorations. Does anyone have any idea what happened here? I tried reinstalling compiz, and that didn't help, so now I have come here seeking advice.

---

### Post by mcduck on 2010-04-24
Compiz is a window manager, so if you run Compiz, then Compiz will be responsible of your window decorations. That's how it's always been. You can't run two window managers at the same time, the two would just fight over control, both trying to manage your windows.

If you want to run Compiz and use metacity themes the correct command for the Window Decoration plugin is "**/usr/bin/compiz-decorator**" (and yes, you must have that plugin enabled if you want to have window decorations at all while running Compiz).

---

### Post by ethanmadden on 2010-04-24
Hmm... that's what it was originally, but it wan't taking metacity's themes... it was just using the big goofy looking compiz theme.I mean, it was using the metacity theme for everything except the minimize/maximize/close buttons, but those were being drawn with the compiz theme.

---

