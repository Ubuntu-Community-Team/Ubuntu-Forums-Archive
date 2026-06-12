---
title: "Programs do not respond on first log in"
date: 2005-12-07
forum: Desktop Environments
---

### Post by jeremie on 2005-12-07
This problem keeps occuring every day, and i can't put a finger on it.

On a typical morning, I open up the computer, log in to Ubuntu Gnome 5.04, launch firefox and check my email. Up to there, everything is fine. 

All of a sudden I notice that i cannot open up any other programs (gaim, xmms, mplayer, etc... even the terminal). The only thing that still works is nautilus. I shut down firefox. Try running other apps. No response. Only the Starting Mplayer.... or Starting Gaim.... appear in the taskbar for a few seconds, and then nothing. 

I would like to give you more details, but i cannot open the terminal to try and launch from there. 

The problem is easily fixed by simply logging out and back in.

For a while, I thought it could be firefox. So i tried loading another program first, instead. Same thing happened. I had to log back in to fix it.

Any suggestion on how to debug this?

---

### Post by 23meg on 2005-12-08
Switch to a virtual terminal (ctrl+alt+f1) and try running a command line program from there after this happens and see if you get any error messagess.

---

### Post by jeremie on 2005-12-08
yes, using the virtual console works for non-graphical apps
such as top, nano, or apt-get

---

