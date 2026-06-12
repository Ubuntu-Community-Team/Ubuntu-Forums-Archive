---
title: "DVD::Rip/MPlayer problem"
date: 2006-01-18
forum: Desktop Environments
---

### Post by Matt Houston on 2006-01-18
I ripped a dvd to an avi file using DVD::Rip, but when viewing it using mplayer there is a 3 inch black strip on the top and bottom of the screen. I did search the forum but couldn't find a solution that works for me. 

I have some avi files which play fine in mplayer, which makes me think it's some setting when I ripped the file using DVD::Rip.

Any thoughts?

---

### Post by ossi on 2006-01-18
Can you post the command with which you ripped it? Here is what I used:

mencoder dvd://[chapter] -ovc lavc -alang en -oac mp3lame -lameopts vbr=3 -o crumbs.avi

---

