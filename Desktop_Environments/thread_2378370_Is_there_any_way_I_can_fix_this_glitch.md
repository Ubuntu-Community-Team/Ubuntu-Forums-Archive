---
title: "Is there any way I can fix this glitch?"
date: 2017-11-22
forum: Desktop Environments
---

### Post by dcpifhq on 2017-11-22
Hi
So I just dual booted Ubuntu 16.04 (don't want 17.something yet) on my family laptop. And this is what USUALLY happens when I resize windows: [https://www.youtube.com/watch?v=4QJUiDL-UTg](https://www.youtube.com/watch?v=4QJUiDL-UTg)

And this also happens on the LibreOffice splash screen...it basically shows the LibreOffice 5 image and then flickers some black rectangles on the image.

Can anyone help me with this?Thanks in advance.

---

### Post by mc4man on 2017-11-22
Probably graphics driver related.
Install inxi (sudo apt install inxi
Then run this command, post the results in a code box, will be informative to any one trying to help you
```
inxi -Fxz
```

---

