---
title: "Mouse Scrolling adjustments ?"
date: 2005-09-26
forum: Desktop Environments
---

### Post by mobo on 2005-09-26
I figure there must be a way to adjust the number of lines scrollable for the mouse like other operating systems and since it isnt in system / preferences / mouse i would think that a file somewhere needs to be edited..

If so, where and what ?


Thanks for any replies.

---

### Post by mlomker on 2005-09-26
For what application?  Are you referring to the terminal?  Are you using gnome or KDE?

---

### Post by mobo on 2005-09-26
Im referring to firefox and web browsing using the Gnome environment.

---

### Post by mlomker on 2005-09-26
[QUOTE=mobo]Im referring to firefox and web browsing using the Gnome environment.[/QUOTE]

I know what you're talking about now...the scroll rate...and that's a good question.  There is a setting for it in KDE.

---

### Post by mobo on 2005-09-26
Yes, exactly.

---

### Post by mlomker on 2005-09-26
Tried the [ SmoothWheel]("https://addons.mozilla.org/extensions/moreinfo.php?id=357") extension for Firefox?

---

### Post by mobo on 2005-09-26
I'll give it a whirl, thanks very much for your time, speed in assisting and professionalism.

---

### Post by Curlydave on 2005-10-14
Smoothwheel doesn't do it. There's no way to set it in gnome, which is IMO really fooking stupid. It's easy to set up in KDE though. You can however change it for individual programs such as firefox. I just did a clean install for breezy and am trying to remember how now...

---

### Post by promet on 2006-08-10
Heya,

I know you can adjust scrolling details in Firefox at least. type:

[COLOR="Blue"]"about:config"[/COLOR]

in the address window. This will take you to the Firefox Config page.

Use the filter to search for:
[COLOR="Blue"]
"scroll"[/COLOR]

The entry you are looking for is:
[COLOR="Blue"]
"mousewheel.horizscroll.withnokey.action"[/COLOR]

Right click on this and choose:

[COLOR="Blue"]"edit"[/COLOR]

You can change the amount of lines to scroll here. There are also a bunch of other weird scroll control entries there...

;)

---

### Post by lucis on 2006-09-16
Where can a Gnome bug be filed for this issue?

---

### Post by DLWood on 2006-09-24
> **promet said:**
> 

The entry you are looking for is:
[COLOR="Blue"]
"mousewheel.horizscroll.withnokey.action"[/COLOR]

Right click on this and choose:

[COLOR="Blue"]"edit"[/COLOR]

You can change the amount of lines to scroll here. There are also a bunch of other weird scroll control entries there...

;)

When I tried changing the default value of "2", nothing different happened.  I changed it all the way from 0 to 16 with no observable change.  

Are you sure this is the line to change?

---

