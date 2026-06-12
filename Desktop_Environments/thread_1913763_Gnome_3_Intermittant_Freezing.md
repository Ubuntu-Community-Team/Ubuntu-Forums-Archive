---
title: "Gnome 3 Intermittant Freezing"
date: 2012-01-23
forum: Desktop Environments
---

### Post by zengyro on 2012-01-23
Hi there,

I am running Ubuntu 11.10 with Gnome 3. Quite often (several times a day) when using Gnome 3, my computer will lock up and become unresponsive, requiring a reboot. 

This happens quite randomly, but is most likely to happen when internet browising: especially with opening a recently downloaded PDF. But will happen at other times as well. This doesn't happen when I use a Unity session: so i suspect the cause lies with Gnome 3. 

I read somewhere else that by installing Pixmap: the problem can be fixed. I did this, which appeared to work for a while - but the problem has now returned. 

I would like to get to the root cause of the problem. But I am not sure which log files to look at and monitor. Also, is there a way to open the terminal to see what errors Gnome3 is writing to StdOut? 

If anyone has a similar problem and has found a solution, then I am all ears!

---

### Post by Frogs Hair on 2012-01-23
To view errors you can enable the Alt + F2 command prompt . Open keyboard > shortcuts > system to enable the command prompt . Use Alt + F2 and enter the following  ```
lg
``` This will open  "Looking Glass" and errors  can be be viewed from there . To close LG press Esc . 

The Log File Viewer may also display something to help you understand the problem . If there is a proprietary graphics driver available in additional drivers you may want to try installing it .  Both Unity and the Gnome Shell run on top of Gnome 3.

---

### Post by zengyro on 2012-01-23
> If there is a proprietary graphics driver available in additional drivers you may want to try installing it 

I have a somewhat outdated Radeon X1300 card. The driver is up to date on it. The 'Additional Drivers' doesn't find any hardware that needs new drivers. 

> The Log File Viewer may also display something to help you understand the problem

That's just it, I am not entirely sure which log file I should be looking at. Naive question: Is it a matter of looking through all them and checking the time stamp?

I tried using Looking Glass: no errors seemed to crop up when the screen froze. Interestingly the LG window was still usuable while the rest of the desktop was frozen.

---

