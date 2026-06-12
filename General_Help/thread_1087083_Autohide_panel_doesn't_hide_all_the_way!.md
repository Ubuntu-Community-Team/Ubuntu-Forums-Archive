---
title: "Autohide panel doesn't hide all the way!"
date: 2009-03-04
forum: General Help
---

### Post by the8thstar on 2009-03-04
I set my top panel to "Autohide", yet I still have about 5-7 pixels of it showing on the desktop. Is this normal? Is there a way to hide the panel completely?

Thanks for your help.

---

### Post by drelyn86 on 2009-03-04
> **the8thstar said:**
> I set my top panel to "Autohide", yet I still have about 5-7 pixels of it showing on the desktop. Is this normal? Is there a way to hide the panel completely?

Thanks for your help.

I'd say it's normal. However, good question! I'd like to know this too...

---

### Post by the8thstar on 2009-03-04
Ha, I found it myself!

Here's how you can do it:

Alt+F2 and run: **gconf-editor**

In the tree, go to: [B]/ > Apps > Panel > Toplevels > Panel_1
[/B]
Then on the right side of the screen, select **auto_hide_size** and set it to 0.

Voila!

---

### Post by crunchfighter on 2009-03-04
Nice find!  I have to say that I like it sticking out just a little, but it is still juuuuuust a bit to far.

---

