---
title: "Configuring i3wm: default xterm font"
date: 2012-06-22
forum: Desktop Environments
---

### Post by CharlesPavlov on 2012-06-22
Not sure I posted this in the right forum, but here goes.
I'm running ubuntu server 12.04 lts with X11 and i3 as my window manager. 
I can use the shortcut win.key+enter to launch xterm in a new window. I'd like to be able to use that shortcut to launch xterm with a dejavusansmono font instead of the default. 
I can do that from a terminal I've already opened by typing in "xterm -fa dejavusansmono -fs 8". I've even aliased "xterm" to that string and I get the same results. I've made a small executable bash script .doxt.sh that does the same and that works too.
The i3 [documentation]("http://i3wm.org/docs/userguide.html#exec") states that "The exec command starts an application by passing the command you specify to a shell" so I bound win.key+enter to xterm hoping that the alias would kick in and launch xterm with the modified font. It didn't. I tried adding the entire string "xterm -fa dejavusansmono -fs 8" instead of just xterm. Win.key+enter stopped working. Instead I made a small executable bash script containing "xterm -fa dejavusansmono -fs 8" in my home folder and tried to exec that. It launched the terminal, but with default fonts. 

How can I convince i3 to launch "xterm -fa dejavusansmono -fs 8" or otherwise just make win.key+enter give me xterm with my custom fonts?

---

### Post by CharlesPavlov on 2012-06-22
Sorry. Fixed. Just needed to restart i3 :-S
<shamed>

---

### Post by antonsky on 2012-07-16
Hi how did you integrate i3wm into lxde/lubuntu?

---

