---
title: "changing resolution using terminal"
date: 2009-03-02
forum: Desktop Environments
---

### Post by mikedmor on 2009-03-02
I hope this is an easy question.

I know about "xrandr -s 1024x768 -r 60" but im using the NVIDIA X Server Settings and the settings will only change in that app. is there a way to change the resolution using Terminal other then that code? Here is what i get when i use it:
```

$ xrandr -s 1024x768 -r 60
Rate 60.0 Hz not available for this size
```

and i can take out the -r 60 and it seems to work but my resolution doesnt change. any ideas?

---

### Post by blackened on 2009-03-02
When you use the -s switch xrandr tries to match the resolution you specify to one listed in the size-index (the list you get when you type xrandr with no modifiers). If the refresh rate you imply with -r is not listed with that resolution in the size-index, then xrandr will error as you've seen.

What resolution are you currently using? You might need to create a modeline and add that to xrandr's size-index to get your desired resolution/refresh.

---

### Post by mikedmor on 2009-03-02
oh i found an auto resolution option in the nvidia panel that fixed it

---

