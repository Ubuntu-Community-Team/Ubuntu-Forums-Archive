---
title: "Tuxracer compilation troubles"
date: 2005-10-02
forum: Gaming &amp; Leisure
---

### Post by bhagabhi on 2005-10-02
Trying to compile Tuxracer I come to problems like these:
game_config.c:784:24: pasting "." and "bool" does not give a valid preprocessing token
game_config.c:784:24: pasting "." and "use_cva" does not give a valid preprocessing token
game_config.c:785:25: pasting "." and "cva_hack" does not give a valid preprocessing token
and several other like those - all through the game_config.c file. 
./configure runs through fine after some tweaking - these come during make.
Anybody know how to fix this? 
Is it just some package I am missing or what?

---

### Post by Hobbsee on 2005-10-02
silly question I know, but why are you trying to compile tuxracer?  It's in the repositories...

> sudo apt-get install tuxracer

---

### Post by bhagabhi on 2005-10-02
Oh... :) I am the one who is silly - didn't have all the repositories active - so I didn't find it. 
Many thanks!

---

