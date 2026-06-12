---
title: "Mplayer assistance needed"
date: 2005-08-11
forum: Desktop Environments
---

### Post by dizbah on 2005-08-11
Hello all! I am new to linux and everytime I try to launch mplayer I get the following message:

New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.


Can someone help me please? I know very little about this OS but I am willing to learn. Thank you

---

### Post by bjweeks on 2005-08-12
You need to install mplayer-fonts.
Hope that helps.

---

### Post by dizbah on 2005-08-12
What's the best way to do that?  Is there a specific command I can type in terminal or a program I can download?

---

### Post by Rhawi Dantas on 2005-08-12
You can install with synaptic... just add the the keyword there...
OR
You can go in the shell and type: sudo apt-get install mplayer-fonts

work both ways :)

---

### Post by dizbah on 2005-08-12
Excellent!  I no longer get the error message at startup, however now when I paste a URL for a radio station that would normally use windows media player, it doesn't do anything....I checked the volume settings and I still don't hear anything.  Please advise!

---

### Post by Rhawi Dantas on 2005-08-12
I don't know :P
But you could start mplayer in the shell and do the same steps that you did to paste the url... And, if there's an error, it will appear at the prompt... Then you can ask again or google it :P

---

### Post by dizbah on 2005-08-12
OK, the latest issue I have now is that when playing a DVD I get a message:  Unable to open VMG....what next?

---

### Post by bjweeks on 2005-08-13
You need to install libdvdcss2. I suggest that you look at [Ubuntu Guide](http://ubuntuguide.org) before asking in the forums.

---

