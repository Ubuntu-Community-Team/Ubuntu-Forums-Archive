---
title: "Mac-sided buttons on other Gnome themes?"
date: 2010-12-26
forum: Desktop Environments
---

### Post by bobmatino17 on 2010-12-26
Well, i just installed Ubuntu Ultimate, and I found a theme I really liked that goes by the name "Azenis". However, I like the button arrangement on the default theme. Is there anyway to get the buttons on the left side of the screen, but still keeping the same look? I uploaded two screenshots just in case there is any confusion on the topic. (The blueish theme is Azenis, the default looking one is well, the default theme.)

---

### Post by mcduck on 2010-12-26
Sure, and rather easily as well.... ;)

Hit Alt-F2 and run "gconf-editor". Then use it to browse to apps/metacity/general, and change the "button_layout"-key to "close,minimize,maximize:"

The problem with doing this with the theme you are using is that it will simply reorder the buttons and move them to different place, it *won't* flip the images used in the theme. As the buttons in your theme are quite different from each other, the theme probably won't end looking very nice. For a good result with that kind of theme you'd have to edit the theme itself, and flip the images to fit the new layout using Gimp or some other image editor...

---

### Post by haircat on 2010-12-26
You can do that with ubuntu tweak easily. 

haircat

---

### Post by bobmatino17 on 2010-12-26
Thank you for your help, by any chance do you know where the image files are stored so I can flip them?

---

### Post by mcduck on 2010-12-26
> **bobmatino17 said:**
> Thank you for your help, by any chance do you know where the image files are stored so I can flip them?

Depends on how you got that theme.

If it came included by default with Ultimate, then you should find it in /usr/share/themes.

And if it's something you've installed yourself, you'll find it in ~/.themes.

---

### Post by bobmatino17 on 2010-12-26
Thank you again for your help.

---

