---
title: "screen resolution problems"
date: 2007-10-22
forum: Desktop Environments
---

### Post by timay91 on 2007-10-22
hey guys I just upgraded to gutsy from feisty the other day and my screen resolution is now 800x600 when it should be 1024x768. so my question is how do I get it back to its proper resolution i tried doing it through the graphics and screen reolution window but it always reverts back to the 800x600 mode.

---

### Post by TeaSwigger on 2007-10-23
Hello, keep in mind when seeking technical help, it's always good to post the context like which version - ubuntu, kubuntu, xubuntu, and all that buntu - and about the computer like what graphics card it is in what computer etc. Detail some steps like, Does it go to 1024x okay? Then it goes back to 800x when you restart the computer? Sometimes there are different things that could do something and people just scratch their heads and move on, especially when its busy soon after a new version like now.

So assuming it was working fine before the upgrade; had you installed any special graphics related stuff in Feisty? Like... 915resolution or xorg-intel or whatever. Possibly you need to redo those steps for the new upgrade? 

Is your monitor identified right? The right model etc.

You may need to edit /etc/X11/xorg.conf which stores the graphics configuration, but if you're unfamiliar, do searching and ask any questions. Mind to always make a safety backup of that file first and be careful, wrong settings can prevent a successful boot so you'd be stuck at command-line until you correct the file (or restore the backup). Sorry I can't be more exact working from ubuntu as I've seldom used it. Luck :)

---

