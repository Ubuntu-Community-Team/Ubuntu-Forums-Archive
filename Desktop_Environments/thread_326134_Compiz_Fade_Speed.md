---
title: "Compiz Fade Speed?"
date: 2006-12-27
forum: Desktop Environments
---

### Post by lorenzo on 2006-12-27
Hi all,
I really like compiz fade effect but after few minutes I feel seasick! The fade effect is **too slow**!!!!!!!!

I've set the speed at the max. value (10.0) in gconf-editor but still..... *seasick*!

Does anyone knows it is possible to speed it up a little more?

Many thanks,
Lorenzo

---

### Post by bekirserifoglu on 2008-03-15
open gconf-editor and go to
```
/apps/compiz/plugins/fade/screen0/options
```
ans set fade_speed to 25.

it will sure be faster.

Alternatively you can use the window match setting to set effects for specific windows.

hope it works.

---

### Post by strabes on 2008-03-15
Why don't you just disable fading? Install compizconfig-settings-manager. Then access it in System -> Preferences, go to "Animations" then Focus Animation, and delete it.

PS: Good to find someone else who gets seasick from compiz, haha. I can barely handle the "normal" setting.

---

