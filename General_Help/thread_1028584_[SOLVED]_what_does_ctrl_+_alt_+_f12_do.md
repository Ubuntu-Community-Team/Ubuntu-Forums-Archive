---
title: "[SOLVED] what does ctrl + alt + f12 do"
date: 2009-01-02
forum: General Help
---

### Post by thingy87654321 on 2009-01-02
when i press ctrl + alt + f12 my screen turns black and the blinking line appears, what does that command do?
it happens on most linux distos i have used, pressing ctrl + alt + f7 turns it back to normal, mandriva does this, ubuntu does this, damn small linux does this (but wont recover back into gui), red hat does this, suse linus does this, what does that command do.
it does come in handy tho, like when you dont want some to see what you are doing :lolflag:

please give me a response as soon as possible, it is really driving me crazy to figure out what it is suposed to do

---

### Post by jerome1232 on 2009-01-02
On Ubuntu ctrl+alt+F1 through F6 are tty's (consoles), ctrl+alt+F7+ are resevered for X sessions, other users can log into X sessions on the tty's above tty7. I believe tty12 is just kept blank, I'm not sure what it's actually for.

---

### Post by SteveDee on 2009-01-02
Hit <ctrl><alt><F12> and you get a blank screen with a blinking curser.

Now hit <alt><F2> and you can log on as a user and do command line stuff.

---

### Post by mcduck on 2009-01-02
Like jerome1232 said, TTYs from 1 to 6 are used for text consoles, TTY-7 is the first running graphical session and the rest are for additional running X sessions. Start a second X session and it will run in TTY-8, accessible with Ctrl-Alt-F8, the next one in TTY-9 and so on. Since nothing is currently running on TTY-12 you only get an empty screen. If you had 6 running X sessions the last one would be at TTY-12.

---

