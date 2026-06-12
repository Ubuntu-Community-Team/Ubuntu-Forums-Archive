---
title: "Doesnt the &quot;Kill process&quot; window have unique ID?"
date: 2012-04-16
forum: Desktop Environments
---

### Post by Leeteq on 2012-04-16
Hi all, I am on Ubuntu 10.04 LTS, using Gnome 2.
Whenever one application "might" be problematic so that I might want to "kill" it, I normally open a "Kill process" window for that, selects "Always on top" and "Always on visible workspace". Then, even if the main System Monitor window seems inactive, it is still possible to minimize it (annoying that it is not possible to use it with such "Kill/Stop" dialogs open, btw), and I just do that so that both windows gets minimized. Works well. If the problematic application needs to be forced off, I can get to that Kill window quickly. This is especially useful if having for example a sporadic memory leak that triggers an uncontrolled memory usage so that the computer almost stop responding. Unless such a window is already available, it can take 20 minutes just to get to the System Monitor, find the process, open such a window, if the computer is racing along into the black hole of a memory leak.

However: here is the question:
I would like to set Compiz to automatically detect such "Kill process" windows and apply the "Always on visible workspace" and "Always on top" options so I dont have to do that each time. This seems not possible, no title or ID on those windows? And even if possible, would such an ID change each time, or could a "kill process" window for just "application-A" be autodetected?

---

### Post by zombifier25 on 2012-04-16
If you are referring to the kill dialog in gnome-system-monitor, then the kill dialog has the same name as the main one, different type however. So you can use the Windows Rules plugin and add this ```
(type=Dialog) & name=gnome-system-monitor
``` to Non minimizable windows, Above and Sticky. Note that when you minimize the main windows the dialog will get minimized also, so you don't need to minimize the main window, just keep it below the windows you're focusing.
Hope this helps.

---

### Post by Leeteq on 2012-04-16
Yes, thanks. That works. Do such dialogs have "Window ID"? Will it be  different each time, or can one particular application's Kill-Process  dialog be identified across sessions?

---

