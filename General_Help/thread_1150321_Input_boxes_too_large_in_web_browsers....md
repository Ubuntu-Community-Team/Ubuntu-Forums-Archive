---
title: "Input boxes too large in web browsers..."
date: 2009-05-06
forum: General Help
---

### Post by monkeys on 2009-05-06
My input boxes, drop-down boxes, and buttons are appearing too large - as if a border has been added around all of them. The background image usually is aligned to fit the text area and on other computers it still looks this way.

I'm not sure what has caused this to occur -- but it is not an issue alone to Firefox, as the issue has repeated itself in Seamonkey and Epiphany.

But prior to noticing this issue, I did the following:
[LIST]
[*]Altered fonts in Appearances menu and altered Font Rendering
[*]Switched my theme, again in Appearances menu
[*]Installed Mac fonts (here: [http://www.ubuntu-unleashed.com/2008/05/howto-install-mac-fonts-on-ubuntu.html](http://www.ubuntu-unleashed.com/2008/05/howto-install-mac-fonts-on-ubuntu.html))
[/LIST]

All these items I've made attempts to undo, to single out the problem, but to no avail. I know it is a minor issue, but as a web developer, it's helpful to know that my coding isn't off! It's a system issue!

---

### Post by mb_webguy on 2009-05-06
Is it only for that site?  The last time I saw controls that looked like that, it was due to a stylesheet.

---

### Post by monkeys on 2009-05-06
I am tempted to think it's a stylesheet issue, but on my sister's Vista laptop it looks fine looking through the same browser. Also, it looked fine before I muddled around with my settings.

Thanks for the reply.

---

### Post by prem1er on 2009-05-06
Are you using a custom theme with ubuntu?

---

### Post by monkeys on 2009-05-06
Yes, I am. But I altered the theme back to "Human" and restarted Firefox with no change.

---

### Post by crom.osec on 2009-05-06
try this:
in firefox address bar type:
about:config
in filter bar of the config page type:
layout.css.dpi
You probably have the value -1
try setting 96

---

### Post by monkeys on 2009-05-06
Thanks, but no luck.

I don't understand what happened or why it chose to manifest itself last night, but I've just altered the CSS so it looks better on my computer. I didn't write the code myself, so maybe mb_webguy's right. Just odd.

Thanks everyone. (:

---

