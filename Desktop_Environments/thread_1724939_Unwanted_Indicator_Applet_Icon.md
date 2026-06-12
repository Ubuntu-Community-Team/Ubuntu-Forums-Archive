---
title: "Unwanted Indicator Applet Icon"
date: 2011-04-09
forum: Desktop Environments
---

### Post by Jeff Root on 2011-04-09
In 64-bit Meerkat there are two buttons in the panel indicator
applet which seem to go together.  One is the power button, that
lets me shut down, restart, and so forth.  The other, immediately
to the left of the power button, is an icon of a speech balloon,
with options: Available, Away, Busy, Invisible, Offline (all of
which are greyed out), Chat Accounts... Broadcast Accounts...
and Ubuntu One....  I would like to get rid of this icon/button.
Is there a way?
 
   -- Jeff, in Minneapolis

---

### Post by Soulcage on 2011-04-09
Right click, remove from panel.

---

### Post by Jeff Root on 2011-04-09
That removes BOTH icons/buttons.
 
   -- Jeff, in Minneapolis

---

### Post by Krytarik on 2011-04-09
To remove only the status part:
```
sudo apt-get purge indicator-me
```
I, too, removed it, although I am using an instant messenger (Pidgin), to save a lot of panel space.

Greetings.

---

### Post by Jeff Root on 2011-04-09
Thank you.
 
Of course, right *after* replying to Soulcage, I looked to
see if what I said to him was correct, and discovered in the 
"Add to Panel" window that the thing is actually called the
"Indicator Applet **Session**", distinguishing it from the
similarly-named Indicator Applet, which contains the audio
and mail buttons.  And discovered that a different button,
"Shut Down", can be put on the panel instead of Indicator
Applet Session, which does all I need.  It has a prettier,
easier-to-see icon, which doesn't fit in with the other
icons.  I'll either have to make it more homely or find
prettier icons to replace all the others.
 
   -- Jeff, in Minneapolis

---

### Post by Krytarik on 2011-04-09
Well, I prefer the "indicator-session", because it
- additionally offers to log out of the session and other options
- fits the other indicators
- has a menu.

---

### Post by Jeff Root on 2011-04-09
And, I see, removing the Indicator Applet Session causes
Shut Down, Log Out, etc. to appear on the System menu, even
though I replaced those functions with the Shut Down applet.
 
   -- Jeff, in Minneapolis

---

### Post by Krytarik on 2011-04-09
> **Jeff Root said:**
> And, I see, removing the Indicator Applet Session causes
Shut Down, Log Out, etc. to appear on the System menu, even
though I replaced those functions with the Shut Down applet.
 
Yeah, exactly.

---

