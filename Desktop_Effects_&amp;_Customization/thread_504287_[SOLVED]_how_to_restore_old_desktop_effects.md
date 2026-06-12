---
title: "[SOLVED] how to restore old desktop effects?"
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by tarek on 2007-07-19
Hi, I installed compiz fusion and now want to remove it and restore the original desktop effects that came with FF.

I installed compiz fusion using this how-to: [http://ubuntuforums.org/showthread.php?t=481314&highlight=remove+compiz+fusion](http://ubuntuforums.org/showthread.php?t=481314&highlight=remove+compiz+fusion)

How do I restore it?

Thanks,
TK

---

### Post by 5-HT on 2007-07-19
Just uninstall all of the packages the guide directed to install, install all of the packages the guide directed to uninstall, and enable desktop effects from the menu. It may be a good idea to reenable metacity prior to doing this (metacity --replace, or just kill off compiz).

Cheers,

---

### Post by tarek on 2007-07-19
tried that but didn't work :( It was working before fusion.

---

### Post by ubanchaos on 2007-07-19
uninstall then reinstall ...so ur just re doin it

---

### Post by 5-HT on 2007-07-19
> **tarek said:**
> tried that but didn't work :( It was working before fusion.

Any errors? If there are no remnants of fusion left, all _should_ be as it was  unless something else is interfering.

---

### Post by tarek on 2007-07-19
That's what I did but it still isn't working.

I installed these packages:
compiz         
compiz-gnome    
compiz-plugins  
compiz-core    
compiz-gtk      
desktop-effects

Am I missing something?

---

### Post by tarek on 2007-07-19
```
$ compiz --replace
Segmentation fault (core dumped)
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display localhost:1.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

That's the output, any ideas?

Thanks again,
TK

---

### Post by macogw on 2007-07-19
Wrong forum.  This should be in Desktop Effects & Customization, not in Beginners.  This isn't a "beginner" topic.

---

### Post by meborc on 2007-07-19
i would suggest killing off x before starting to mess with meta and compiz... boot into recovery and remove the packages you need to remove... then install the ones you removed in the how to... it might be a good idea to install the ubuntu-desktop metapackage just to be sure you have all you had in the initial install...

---

### Post by tarek on 2007-07-19
Nevermind, I'll just leave it the way it is or reinstall fusion.

Thanks everybody,
TK

---

### Post by hyperair on 2007-07-19
There's a thread somewhere which I've posted in before, detailing a howto on removing Compiz Fusion and restoring the old Compiz. Can't remember where it is though.

---

### Post by eClaW on 2007-07-29
[SOLVED] ? I've currently got the same problem but how is something solved in this thread? Well, guess I'll keep on looking...

---

### Post by tyreck on 2007-07-30
I've got all of my Beryl settings back to normal as far as i can tell

Compiz-Fusion screwed them all up (must share config data or something)

however, when i installed compiz-fusion (was previously running Beryl and Emerald)

it removed the color from my emerald theme, not liking that (that and you can't set ALT+Tab as ring switcher keys) i removed Compiz-Fusion and reloaded Beryl and emerald.

same thing, emerald theme isn't semi black glassified anymore, just completely transparent

it seems to do that to any theme that has the glassify effect, solid borders are ok.

anyone have any ideas how i can get my theme to load correctly again?

---

