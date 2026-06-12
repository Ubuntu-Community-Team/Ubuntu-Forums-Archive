---
title: "Activate keys"
date: 2011-10-18
forum: Desktop Environments
---

### Post by canhoto on 2011-10-18
Do you know how can we activate the 3rd level with a specific key, or define the alt, win, etc. behaviour, on the keyboard on Xubuntu 11.04? I don't see the options in the keyboard settings

---

### Post by Chonnawonga on 2011-10-21
I'm no expert in this, but I've been trying to figure out similar issues, and this is what I've come up with.

Open up your /etc/default/keyboard file:
```
sudo leafpad /etc/default/keyboard
```

You'll see a line like this:
```
XKBOPTIONS="lv3:ralt_switch"
```

That's the one you want to play with. I don't know exactly what the options are, but I just deleted everything within the quotation marks to stop using the right alt key as a third-level chooser. 

There are two important things to note:
1. Note that you must restart for changes to take effect!
2. There's another file in the default directory called "console-setup" which includes the same options. I don't know why this stuff is duplicated, but it is.

If anyone has more information or a better solution, I'm all ears!

---

