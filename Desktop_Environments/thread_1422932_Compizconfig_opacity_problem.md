---
title: "Compizconfig opacity problem"
date: 2010-03-06
forum: Desktop Environments
---

### Post by crashus on 2010-03-06
Hey! I have a problem that I created by my own foolishness:) 

When adjusting the opacity for windows panels in compizconfig settings manager, I also wanted to have the compiz manager transparent a bit. When i clicked on the manager window, to add it, I had the default opacity settings set to 0- so the manager instantly dissapeared, as it is now completely transparent. 

Is there a way to reverse this without losing all of the others settings I have already made using compiz? If I reinstall I would probably lose every setting and I really don't want to do that, because I've spent too much time getting it just the way I like it.....:)


Anyone know a way to help me?

Thanks!

---

### Post by crashus on 2010-03-06
Any ideas?

---

### Post by asmoore82 on 2010-03-07
:lolflag: I did a similar thing a couple weeks ago.

IF you are using the gconf backend to compiz, you can turn off all opacity rules like this:
```
gconftool-2 --unset "/apps/compiz/plugins/obs/screen0/options/opacity_matches"
```

---

### Post by crashus on 2010-03-07
yep that did it:)!

Thanks for halping me! And I'll try not to do sth so stupid again:::D!

---

