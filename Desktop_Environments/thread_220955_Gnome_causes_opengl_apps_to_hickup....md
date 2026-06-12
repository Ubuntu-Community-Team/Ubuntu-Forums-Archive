---
title: "Gnome causes opengl apps to hickup..."
date: 2006-07-22
forum: Desktop Environments
---

### Post by kreso on 2006-07-22
I really don't know why, but all my opengl apps "hickup" every second when I'm running them under GNOME. By hickuping I mean, the prog runs slower and then stops for a btief moment and continues, and so on every second.

I did not experience this problem when I first installed ubuntu, but seems to happen on all distros after a while. Oddly enough, opengl apps run just fine on KDE,xfce and other DM's.

---

### Post by Anduu on 2006-07-22
I bet something running in the background is causing this....

One time I installed the Network Manager app from the repos and suddenly Quake3 started "hiccupping"...every other second the framerate would take a 50 point drop and there was a noticeable hitch...

I removed Network Manager as I didn't really need it and all was good again.

To get an idea of what might be causing this use the top command at the console and keep an eye on the CPU column and see if there are regular,high spikes in processor usage.

If nothing seems unusual there I would suspect your OpenGL drivers aren't set up correctly.

---

### Post by kreso on 2006-07-22
hmm, it might be the network manager, I'll try removing it. Anyway, the drivers are fine as they are working ok under xfce.

---

