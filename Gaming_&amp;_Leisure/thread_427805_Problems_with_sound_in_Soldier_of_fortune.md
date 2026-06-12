---
title: "Problems with sound in Soldier of fortune"
date: 2007-04-29
forum: Gaming &amp; Leisure
---

### Post by gardara on 2007-04-29
I just installed Soldier of fortune linux version 1.04 (with loki installer).
The game works really well except the sound isn't working.

Can anyone help me with this? The game isn't really fun when you don't have any sound :(


Thanks in advance :)

---

### Post by noerrorsfound on 2007-05-05
I found this thread because I was originally having the same problem. Since you didn't paste the terminal output (open a terminal and then run the game from within it so the terminal doesn't close) I can't see what error(s) you're getting.

I just had to restart to fix it, but on some games I used:
```
sudo killall esd
```
On this one it didn't work for me, however, so perhaps it was something else. I just restarted Ubuntu and it worked.

---

