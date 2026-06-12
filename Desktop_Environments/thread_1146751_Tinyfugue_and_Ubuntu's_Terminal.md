---
title: "Tinyfugue and Ubuntu's Terminal"
date: 2009-05-02
forum: Desktop Environments
---

### Post by Dragonmantank on 2009-05-02
I recently switched my home server over from CentOS to Ubuntu 9.04 (only reason was because I put in an Atheros wifi card that CentOS was having fits with). From this machine I run Tinyfugue under screen.

On CentOS, it would properly redraw the screen whenever I resized my terminal and the PageUp button would work to scroll back through the game history, and the Up arrow key would scroll through the input window.

On Ubuntu, whenever I resize my terminal (xterm, gnome-terminal, or puTTY on Windows) all the world history is lost once the screen redraws and the PageUp button does not scroll, it outputs '[[5~' into the lower input window, and the up arrow key doesn't do anything. This behavior happens both inside and outside of 'screen'.

I'm sure that this is just a terminal setting, but I have no idea what, and since I didn't think it would be a problem I didn't bother checking to see what my terminal settings where under CentOS (they were whatever CentOS sets as the default settings).

If anyone has any ideas, I'd really appreciate it.

---

