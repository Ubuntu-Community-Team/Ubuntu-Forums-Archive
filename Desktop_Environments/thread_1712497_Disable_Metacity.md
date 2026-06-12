---
title: "Disable Metacity"
date: 2011-03-22
forum: Desktop Environments
---

### Post by Shadow21 on 2011-03-22
I just installed Firefox 4 and I really like how it looks without the title bar (the bar with the close button) so is there a way for me to disable that only for Firefox? I'm guessing that I would have to disable Metacity for Firefox somehow.

---

### Post by Copper Bezel on 2011-03-22
Do you have ccsm installed?

If so, open Compiz Config Settings Manager and go to "Window Decoration."

Under Decoration Windows, enter

(!name=Navigator)

To keep the frame except when maximized, use this instead:

!(name=Navigator & state=Maxhorz & state=Maxvert)

---

### Post by Shadow21 on 2011-03-22
> **Copper Bezel said:**
> Do you have ccsm installed?

If so, open Compiz Config Settings Manager and go to "Window Decoration."

Under Decoration Windows, enter

(!name=Navigator)

To keep the frame except when maximized, use this instead:

!(name=Navigator & state=Maxhorz & state=Maxvert)

I added 

!(name=Navigator & state=Maxhorz & state=Maxvert)

To the Decoration Windows field and it didn't do anything. I also enabled Window Decoration.

---

### Post by Copper Bezel on 2011-03-22
Well, I'm using 3.6, and you're using 4.0, so the window name might be different. Let's try this then. Run this command from a terminal:

```
xprop | egrep "(WM_WINDOW_ROLE)|(WM_CLASS)"
```

And click on Firefox. That'll give you the name of the class, which we can also use to identify the window to the Decorations plugin.

Try this string instead in the field first, though: ```
!(class=Firefox & state=Maxhorz & state=Maxvert) 
```
It should be the only thing in the field, because it means that every window that isn't a maximized Firefox will be decorated.

---

### Post by Shadow21 on 2011-03-23
> **Copper Bezel said:**
> Well, I'm using 3.6, and you're using 4.0, so the window name might be different. Let's try this then. Run this command from a terminal:

```
xprop | egrep "(WM_WINDOW_ROLE)|(WM_CLASS)"
```And click on Firefox. That'll give you the name of the class, which we can also use to identify the window to the Decorations plugin.

Try this string instead in the field first, though: ```
!(class=Firefox & state=Maxhorz & state=Maxvert) 
```It should be the only thing in the field, because it means that every window that isn't a maximized Firefox will be decorated.

That didn't work either :-k

This is what I get when I run

```
xprop | egrep "(WM_WINDOW_ROLE)|(WM_CLASS)"
``````
WM_WINDOW_ROLE(STRING) = "browser"
WM_CLASS(STRING) = "Navigator", "Firefox"

```

I've been messing around with different Window Decorations and I haven't been able to get it to work.

---

### Post by nknwn666 on 2011-03-23
add ```
!title=Firefox
``` in the Decoration windows in Window decorations settings in CCSM, thats what i did and it works perfect

---

### Post by Copper Bezel on 2011-03-23
Weird. Since the class string *does* include "Firefox", that should have worked.

> **nknwn666 said:**
> add ```
!title=Firefox
``` in the Decoration windows in Window decorations settings in CCSM, thats what i did and it works perfect

That's a bit of a brute force method. It'll apply to non-maximized Firefox windows, including preferences and settings windows, as well as anything with "Firefox" in the titlebar. Opening a .pdf named "The Wondrous World of Firefox" would cause Adobe Reader to lose window decorations.

---

### Post by Krytarik on 2011-03-23
> **Copper Bezel said:**
> ```
!(class=Firefox & state=Maxhorz & state=Maxvert) 
```
I can confirm that those window match works. Of course you need to run Compiz' (desktop effects) for that to have any effect. Is that the case? And it only removes the title bar of maximized Firefox windows, like *Copper Bezel* said, which makes totally sense. If you want to remove the title bar of *any* Firefox windows instead, use this window match:
```
!class=Firefox
```

---

