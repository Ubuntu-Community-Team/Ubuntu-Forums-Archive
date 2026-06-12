---
title: "compiz makes gnome-terminal TOO transparent (can see desktop icons)"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by exodunix on 2007-11-24
this appears to be something compiz does because I have my session set to open up a terminal when i first login, and that terminal's transparency only shows the desktop wallpaper (how i like it), however, the next terminal i open up is TRULY transparent, meaning i can see all windows behind it and desktop icons and so on.

i've attached a screenshot

i've searched and searched for an answer but can't seem to find one.

56k warning[
[http://www.unix.to/images/Screenshot-1.png](http://www.unix.to/images/Screenshot-1.png)

---

### Post by FuturePilot on 2007-11-24
Open a terminal window and go Edit>Current Profile. Click on the Effects tab, and there you can adjust the transparency. The Gnome Terminal is Composite Aware. Without Compiz if you set some transparency to the terminal it is pseudo transparency. But since it is Composite Aware, once you activate Compiz, it becomes aware of the compositing, and then uses true transparency.

---

### Post by exodunix on 2007-11-24
> **FuturePilot said:**
> Open a terminal window and go Edit>Current Profile. Click on the Effects tab, and there you can adjust the transparency. The Gnome Terminal is Composite Aware. Without Compiz if you set some transparency to the terminal it is pseudo transparency. But since it is Composite Aware, once you activate Compiz, it becomes aware of the compositing, and then uses true transparency.
I see, well, is there anyway to change it back to psuedo transparency? I actually like it better.

I just did a quick google, it seems most people are working *towards* true transparency. no luck on finding a solution

---

### Post by FuturePilot on 2007-11-24
Sorry, the only way would be to turn Compiz off I think.

---

### Post by Forlong on 2007-11-24
> **exodunix said:**
> I see, well, is there anyway to change it back to psuedo transparency? I actually like it better.
Then you might as well use a background image.

---

