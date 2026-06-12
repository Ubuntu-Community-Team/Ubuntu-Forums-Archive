---
title: "Custom mouse pointer dissapeared"
date: 2009-04-26
forum: General Help
---

### Post by Svensk023 on 2009-04-26
Hi, 
I installed a custom mouse cursor the two days ago after my fresh Jaunty install and it worked just fine. But after a few reboots it went missing and now I have the default mouse cursor again. So I tried to re-install the custom cursor but it keeps giving me an error message saying

"Installation for theme failed, cannot move directory over directory"

I looked in /etc/X11/cursors and couldn't find the custom cursor theme. So frankly I am stumped. Any suggestions?

I am running the 64-bit version of Jaunty if that matters.

---

### Post by scry on 2009-04-26
The files of your cursor are probably located in /home/yourname/.icons 
try deleting them and reinstalling the theme.

---

### Post by Svensk023 on 2009-04-26
thank you, that did the trick

---

