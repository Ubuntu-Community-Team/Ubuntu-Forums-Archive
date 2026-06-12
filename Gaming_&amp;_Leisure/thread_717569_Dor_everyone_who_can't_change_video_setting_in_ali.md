---
title: "Dor everyone who can't change video setting in alien arena 2008's VIDEO mebu"
date: 2008-03-07
forum: Gaming &amp; Leisure
---

### Post by eragon100 on 2008-03-07
Hi everyone!

I had this "problem" with alien arena 2007 as well: I can't change the settings in the video menu, because changing any of them and clicking apply immediately crashes the game, which doesn't save the changes. Since if i have a default ubuntu 7.10 install and a nvidia geforce 7 video card, I can't believe I am the only one who encounterd this issue. In /home/username/.codered/arena there is a config file. Open it and change the options there. For example, to activate bloom, simply change the R_bloom option (or something like it) from a 0 into a 1. Save the file and start the game. It will start nd run coorectly with the settings you put in the config file. Enjoy! :)

---

### Post by marshall.robert on 2008-05-04
for me it was in .alien-arena instead of .codered.

the lines needed to set res are:

set vid_height
set vid_width

---

