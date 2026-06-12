---
title: "Resize workplaces when I click activities"
date: 2022-06-16
forum: Desktop Environments
---

### Post by HappySmack on 2022-06-16
I have a pretty fresh install of 22.04 with proprietary AMD drivers installed.  When I click activities, instead of the expected work-spaces on the right side, I get a tiny single workspace.  I have been able to grab a program window so I know it is a workspace but it is so tiny and unusable.  I have no idea where to resize this.  Any help of a direction to go in would be appreciated.

[IMG]https://i.imgur.com/RF35XzJ.png[/IMG]

---

### Post by HappySmack on 2022-06-16
Like usual, after i search for weeks and can't find an answer, I find it an hour after posting for help.  I had to edit the file ```
~/.local/share/gnome-shell/extensions/vertical-overview@RensAlthuis.github.com/workspaceThumbnail.js
```
And change the value of 'var MAX_THUMBNAIL_SCALE = 0.05' to 'var MAX_THUMBNAIL_SCALE = 0.15'

---

