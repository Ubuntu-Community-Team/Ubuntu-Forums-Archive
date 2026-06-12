---
title: "After Emerald Install, Compiz No Longer Works"
date: 2009-06-04
forum: General Help
---

### Post by deathblossom on 2009-06-04
Hey all, I was trying to install Emerald so that I could use a theme I found, but after installing it and the theme not working right (only the title bar was themed instead of the complete desktop), I tried to switch back to compiz, but then compiz was fubar as well when it worked perfectly before. I attached a screen shot so you can see the problem. All of the screen except a square in the top left is black and while programs will realize this and size/position accordingly, the desktop does not.


 I ran xfix in Recovery Mode and the problem persisted, so looking for any further advice.

---

### Post by mcduck on 2009-06-04
I have no idea what's causing your current problem, but I just had to pop in to tell you that Emerald is not even supposed to change anything else than window borders.. ;)

Try running "metacity --replace" to at least get a functioning desktop.

---

### Post by deathblossom on 2009-06-04
Oh really? Whoops! Haha, I was browsing gnome-look looking for something new and it was under Emerald themes, so I assumed the whole thing was supposed to be theme not just the window border.

I've got it running with metacity now, although even that is operating differently than it used to - almost as if some of compiz is still running, because Gnome Do works okay, when it used to appear totally screwed without compiz.

Also, really sorry I created this in the wrong section.

---

### Post by deathblossom on 2009-06-04
Ah well, I fixed it. Went to Compiz Settings and checked Detect Outputs. I'd unchecked a bit back fooling around trying to fix my VGA problem, which turned out to be a kernel problem. Sorry!

---

