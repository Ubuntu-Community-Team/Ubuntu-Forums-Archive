---
title: "Move mouse pointer to fixed spot?"
date: 2011-03-31
forum: Desktop Environments
---

### Post by ThomasJ02 on 2011-03-31
I have a pretty large screen setup (3 wide x 2 high), and it frequently takes me a few seconds to "find" my mouse pointer when I first sit down at my box. Is there a way to move the mouse pointer to a predefined location, for instance when I press a hotkey combination? Or maybe some way to flash the mouse pointer so it's easier to find?

---

### Post by hictio on 2011-03-31
> **ThomasJ02 said:**
> 
~snip~
Or maybe some way to flash the mouse pointer so it's easier to find?

Have you checked:

System > Preferences > Mouse

"Show position of pointer when the Control key is pressed"

---

### Post by patryk77 on 2011-04-01
> **ThomasJ02 said:**
> Or maybe some way to flash the mouse pointer so it's easier to find?

If you use Compiz, install compizconfig-settings-manager and access it under System/Preferences.

I forget what it's called, but there is a plugin that highlights the mouse on a key combo press... Looks very nice, I use it on my LCD TV when I sit far

Edit: It's called show mouse and the default key is Super+K

---

### Post by stinkeye on 2011-04-01
> **hictio said:**
> Have you checked:

System > Preferences > Mouse

"Show position of pointer when the Control key is pressed"

Didn't know about that one.Thanks.
All good solutions here.

Another one is to install **xdotool** and bind a keyboard shortcut to
```
xdotool mousemove 0 0
```
which will move the mouse cursor to the top left corner.

---

