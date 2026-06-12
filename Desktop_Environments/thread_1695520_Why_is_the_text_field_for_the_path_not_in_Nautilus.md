---
title: "Why is the text field for the path not in Nautilus anymore?!"
date: 2011-02-26
forum: Desktop Environments
---

### Post by billdotson on 2011-02-26
Why do you have to press ctrl-L to use the location text box in Nautilus? There used to be a setting in preferences where you could have it always use the text bar. Now you have to use some gconf command in the terminal. The gconf command I've used also will only work for normal users. If I want to open a root nautilus terminal to move files around between my mounted drives then I have to hit ctrl-l every time.

It is really annoying because if I am in a Nautilus window there are lots of times where I need to copy the path to something I am doing in the terminal.

Why does it seem like everything involved with Ubuntu is simplifying things at the expense of having options? I thought GNU/Linux was all about options. I guess it still is, but I just cannot understand why you would completely remove options instead of just putting them in an advanced section or something.

---

### Post by Krytarik on 2011-02-26
The option is obviously not included in the Preferences dialog, but you can still set it:
- press Alt+F2
- enter "gconf-editor"
- browse down to "/apps/nautilus/preferences/always_use_location_entry"
- tick it

Greetings. ;-)

---

### Post by towheedm on 2011-02-27
> **Krytarik said:**
> The option is obviously not included in the Preferences dialog, but can still set it:
- press Alt+F2
- enter "gconf-editor"
- browse down to "/apps/nautilus/preferences/always_use_location_entry"
- tick it


Yes well that would work for the logged in user.  From what I gather he would like have it enabled for a root nautilus.  To do this, enter:

```
gksudo gconf-editor
```

and change the key mentioned.  Now once you open a root nautilus, the location bar will always be visible.

---

### Post by Krytarik on 2011-02-27
> **towheedm said:**
> Yes well that would work for the logged in user.  From what I gather he would like have it enabled for a root nautilus.  To do this, enter:

```
gksudo gconf-editor
```and change the key mentioned.  Now once you open a root nautilus, the location bar will always be visible.
Yeah, I overlooked the root thing (was a bit tired yesterday), so +1. ;-)

---

