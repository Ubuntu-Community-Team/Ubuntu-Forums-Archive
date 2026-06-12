---
title: "Unwanted &quot;Ubuntu Desktop&quot; appears instead of file menu when hovering over top menu"
date: 2014-06-05
forum: Desktop Environments
---

### Post by hannah6 on 2014-06-05
I tried to check for a cross posting of this and couldn't find anything similar, please correct me if I am wrong.

I am a new Ubuntu user, and when I first installed Ubuntu when I hovered over the top menu where the battery life and other icons are, the file menu for the current window would appear. After installing Unity Tweak app the window spread feature seems to have made it to where when I hover over the top menu, now the bar says Ubuntu Desktop and my current window zooms out like on a Mac when you want to switch windows. I don't like this feature and I'm hoping someone knows how to reverse it. I tried uninstalling the Unity Tweak app and my top menu now shows the file menu if I don't move the mouse too fast to the very top, but if I move it too fast, the same thing happens as before. It's really annoying to have to click out of the window spread feature or whatever it is every time I try to close a maximized window, etc. Anyone know how to make this feature turn off?

Suggestions and instructions are much appreciated. :)

---

### Post by grumblebum2 on 2014-06-05
Sounds like you have enabled a hot corner for window spread.
Uninstalling unity-tweak-tool won't revert anything you may have changed.

Reinstall unity-tweak-tool and have a look in **window manager > hot corners**
You have a **restore defaults** button at the bottom.

Still having problems, then run this command in terminal to reset compiz to defaults...
```
dconf reset -f /org/compiz/
```

Log out and back in.

---

### Post by hannah6 on 2014-06-11
Thanks, that solved my problem!

---

