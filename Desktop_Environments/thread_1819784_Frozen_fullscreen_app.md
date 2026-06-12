---
title: "Frozen fullscreen app"
date: 2011-08-06
forum: Desktop Environments
---

### Post by iraiam on 2011-08-06
I am working on a "media center" project. It is basically a Ubuntu (or variant) computer with the output going to a TV and home theater system.

I would like to know if there is any way to deal with a frozen full screen application with Ubuntu?  Occasionally the media center software freezes, Ubuntu seems to still be running fine but I am unable to get control back from the frozen app, and have to kill it with the power button.

Thanks much

---

### Post by Frogs Hair on 2011-08-06
I was thinking it may be possible to set a key binding to work like the force quit applet , which is impossible to use at full screen.

---

### Post by Bonster on 2011-08-06
To Make a keybinding for force-quit use

> xkill

---

### Post by iraiam on 2011-08-06
Hmmm, I tried but I was unable to make xkill work,  I think because it is designed to kill an X server client.  I am trying to kill a full screen application, there is no window to select.

I also tried pkill and killall, none of which worked, I do have the option to run in windowed mode but that is undesirable. I'll just be careful about opening bad video files until I develop a solution, possibly another Linux distro will be better suited for this.

---

### Post by Luke M on 2011-08-07
Did you try control-alt-F1?

---

### Post by iraiam on 2011-08-07
yes Ctrl+Alt+F1 through F7 do nothing, I think this may be another problem, I installed the media center software on my Ubuntu desktop pc and the tty switching functions properly. I was able to switch to tty1 and manually kill the media center software.

---

