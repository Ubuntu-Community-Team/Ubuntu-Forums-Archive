---
title: "Screen always boots improperly scaled"
date: 2007-03-04
forum: Desktop Environments
---

### Post by Rippy on 2007-03-04
I've had Feisty Herd 4 (and now, Herd 5, but that didn't cause the issue) for a week or two now. But just in the last couple days, it's started doing something funny. When it's starting up, at the point where all I see is my mouse and the background colour, the screen is scaled perfectly (the corners of the screen match the corners of my monitor). However, it then changes the scale after loading some other things. There's a gap of about 1cm around the screen, a black strip of empty monitor space.

I was fooling around with Wine yesterday, and when trying to get Starcraft working, it loaded at 640x480; when I exited, ubuntu reset my resolution back to 1024x768, except that time it was properly scaled.

So basically, the screen isn't scaled properly when I boot, but if the resolution is changed and then is brought back to 1024x768, it scales properly.

Anyone know why this is?

Extra info:
- Running latest repository version of Compiz. However, even with desktop effects disabled, the problem persists
- ATI Radeon 9200 PRO, using open-source driver with AIGLX acceleration

Hope this isn't tough to fix, it's annoying having my screen squished every startup :/

-Rippy

EDIT: I tried switching ubuntu's resolution to 800x600 and back, but that didn't change anything. Hm, I don't know why Starcraft seemed to fix it

EDIT2: If I exit to the login screen, it displays at the proper resolution, it's only once I log in that it goes funny. Also, while I've got a thread opened, there's another minor problem I'd like to find a fix for: on startup, my aMSN window always appears in the same spot, near the middle of the screen. However, I've always had it appear on the right side, which is where I always move it, but it still persists in starting up in the middle. Anyone know why?

---

### Post by Rippy on 2007-03-05
bump?

---

### Post by Rippy on 2007-03-06
um, is there any chance of resolving this?

---

### Post by Rippy on 2007-03-07
I'm gonna bump this one more time. Please, does ANYONE have a fix for this??

---

### Post by superzorro on 2007-07-10
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=19366&amp;highlight=black+strip](http://ubuntuforums.org/showthread.php?t=19366&amp;highlight=black+strip) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I don't know if you figured out, I had the same problem and I solved it using "xvidtune"

Heres is the post that solved it 

Good luck

---

