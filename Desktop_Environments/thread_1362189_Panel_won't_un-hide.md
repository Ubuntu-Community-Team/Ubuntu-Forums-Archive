---
title: "Panel won't un-hide"
date: 2009-12-22
forum: Desktop Environments
---

### Post by PseudoLemon on 2009-12-22
I have a panel on the side of my screen with the notification area on it. I have it set to auto hide, and now it won't unhide itself. I have no idea why this is happening, but if anyone knows anything that'd be great.

---

### Post by PseudoLemon on 2009-12-22
Never mind I killed it.:)

---

### Post by karthikkln on 2009-12-23
just mak it manually or download the software named pessulas in the synamptic pacakage manager..! and confiurge ur desktop by ur self by using this..!

---

### Post by karthikkln on 2009-12-24
what's tis dude..! u should hav try that..! ny way in future dont skip the things.! try 2 solve that..!!:P :popcorn:

---

### Post by Detailedghost on 2010-05-21
I'm having the same problem with 10.04 unfortunately

---

### Post by thoughtcrime.kid on 2010-12-29
i got this when i upgraded to Maverick, it was hiding to only 1px and it seems like the panels won't un-hide when your cursor is at the edge of the screen.

To Fix: 

-in terminal, run gconf-editor

(this opens an interface through which you can edit your gnome configuration.)

navigate to apps>panel>toplevels>panel_0

(panel_0 is the default name of a new panel, yours may vary.)

-in the right window, change the value of auto_hide_size to a larger number

(not too large. i went with 5px)

-log out, log in, should work

---

### Post by TeagueSterling on 2011-03-04
I was having the same bug and it turned out to be related to Desktop Wall edge flipping. As soon as I disabled edge flipping everything went back to normal.

---

### Post by Copper Bezel on 2011-03-04
Yeah, I've seen this, too. If any Compiz plugin is assigned to a screenedge, a panel on that edge won't return from autohide, because Compiz captures the hover.

---

### Post by Krytarik on 2011-03-04
Good to know! I was already wondering why I always have to *seek* it with gconf-editor after trying its autohide feature.:P
However, since I don't really like the behaviour of the feature I didn't really bother.

Greetings.

---

### Post by gorg0th on 2011-04-25
> **thoughtcrime.kid said:**
> i got this when i upgraded to Maverick, it was hiding to only 1px and it seems like the panels won't un-hide when your cursor is at the edge of the screen.

To Fix: 

-in terminal, run gconf-editor

(this opens an interface through which you can edit your gnome configuration.)

navigate to apps>panel>toplevels>panel_0

(panel_0 is the default name of a new panel, yours may vary.)

-in the right window, change the value of auto_hide_size to a larger number

(not too large. i went with 5px)

-log out, log in, should work
Thanks kindly for this tip, helped me perfectly.

---

