---
title: "Bottom panel of desktop went haywire"
date: 2011-07-19
forum: Desktop Environments
---

### Post by SOMDdan on 2011-07-19
Holy Crap! My computer freaked out, and started opening new windows in the bottom panel by the thousands. The windows didn't open in the main desktop, but the bottom panel filled up with new window icons and kept filling so fast the whole panel became a slithering, pulsing mass of rapidly opening window icons that compressed to the max to fit in the panel. I opened system monitor and both my CPU cores were at nearly 100%. I ran ***top  *****and**a process called something like "gnome-panel" was at the top of the list with over 50% CPU usage. I ran ***kill*** on the PID of that process, and got a bunch of funky popup error messages about the panel reloading (never seen that before), and I was able to finally get the panel to clear out. Now nothing shows up in the bottom panel even when I open a window for Firefox, or open a folder on the desktop. I know there are still open windows, but they don't show up in the bottom panel. Even after restarting the computer nothing shows in the bottom panel. Any ideas on what I killed and how to get the bottom panel back to normal?    I am running 10.04 with the gnome desktop on a old Gateway convertible laptop. The computer has been running Ubuntu for over a year without anything like this happening before.

---

### Post by SOMDdan on 2011-07-19
A follow up question as well: which log file would I go to find out the process I killed, or to find out anything about what was running at the time? Does anyone know of a good list or directory that shows what log file shows what type of event?

---

### Post by SOMDdan on 2011-07-20
I don't know how the crazy window-opening error happened, but I did manage to get back the bottom panel open window icons by using the "add to panel" function and adding the "window list" to the bottom panel.

---

