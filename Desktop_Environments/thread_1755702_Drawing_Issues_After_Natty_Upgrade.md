---
title: "Drawing Issues After Natty Upgrade"
date: 2011-05-11
forum: Desktop Environments
---

### Post by armware on 2011-05-11
I am experiencing a few rendering problems since the upgrade to natty. Everything runs fine (no crashes, lockups or slow downs) but there are still issues present.

KDE v4.6.2
Compiz v0.9.4.0
Amarok v2.4.0
Yakuake v2.9.8

1) yakuake will not redraw itself. if i exit it and relaunch it, i can run one command and see the terminal output. once the command is finished, all drawing updates fail. typing in the next command does not show, though it does run. ie: glxgears will launch, but going back to yakuake does not show it being typed in.

2) yakuake's hide hot key (f12) does in fact hide the window, though it is still drawn on top of everything. clicking around in the app displayed below it causes the app to redraw which 'erases' the drawing of yakuake.

3) amarok's osd prevents anything on the screen from changing (except cursor) while it's displayed, but only when switching to the next track. changing ratings shows the osd and does not have any negative effect. disabling the osd stops this lockup.

4) application launcher seems to be doing the same thing as in issue #1 - after a single click anywhere within it, no more drawing updates so i have no idea what i'm clicking on. this does not always happen, though it's around a 50% chance.

5) application launcher also will not close until i click the panel icon again.

6) device manager eventually fails to redraw. sometimes it fails to even stay open. clicking it (once) causes it to more or less flash on the screen.

7) krunner displays a cutoff of the last time it was used. typing causes it to redraw.


i'll post more as i find them. until then, there seems to be a bigger underlying issue affecting these apps. how can i proceed to finding the cause?

---

