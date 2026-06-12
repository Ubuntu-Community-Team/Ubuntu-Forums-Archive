---
title: "Why windows open in the background when called through keyboard shortcuts?"
date: 2015-09-03
forum: Desktop Environments
---

### Post by Issam2204 on 2015-09-03
I set several keyboard shortcuts, for example CTRL+SHIFT+A opens my  Amazon folder. However, it opens in the background (i.e., behind Firefox  or Chrome).
  
My shortcuts involve gedit, Nautilus, Firefox, Calculator,  Thunderbird, and Terminal (usual, CTRL+ALT+T). Among these, only  Terminal and gedit open in the foreground.

  Why?


  I also tried to check on the Compiz Manager. The option *raise on click* is enabled.


  I'm using Ubuntu 14.04.3 x64, with no Gnome 3 PPA.


  Thank you!

---

### Post by QDR06VV9 on 2015-09-03
I think you are on the right track with the Compiz Settings Manager.
But this is a frustrating ordeal, Try to fool around in General Compiz Options The Tab that says Focus & Raise Behavior there is a Drop-down bar(Focus Prevention Level) I have mine set on Low.
It is not perfect but less annoying, But try a few others to see if one works for your needs or wants.
Kind regards

---

### Post by Issam2204 on 2015-09-04
Hi runrickus! Thank you so much for the hint!

I've set *Focus Prevention Level* on **OFF** and now it works perfectly. Windows raise in the foreground like they are supposed to :)

Thank you again!

---

