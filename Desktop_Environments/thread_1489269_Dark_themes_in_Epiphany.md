---
title: "Dark themes in Epiphany"
date: 2010-05-20
forum: Desktop Environments
---

### Post by kogger on 2010-05-20
Epiphany works fairly well with dark themes overall, but some web pages have text boxes and buttons with black text on a dark background. Not all websites do, and the address bar has light-colored text (as the theme requests), so I have a feeling that it's caused by a hybrid of GTK and website-specific themes being rendered. Anything rendered purely by GTK has a dark background with light text, and websites that seem to have custom-designed components have white background with black text (like Google's search box), but some websites seem to render the component itself with GTK, but get the font color from HTML.

I found in Edit->Preferences->Fonts & Style an option that lets you create your own custom stylesheet, but so far I haven't been able to use it to get text boxes and buttons to render with light-colored text.

Any ideas?

---

