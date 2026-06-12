---
title: "Gnome shell supported css"
date: 2019-12-13
forum: Desktop Environments
---

### Post by 1kivi on 2019-12-13
Hi!
I've been messing around with my gnome shell css, and I'm trying to get some text styled to be all upper case, but the text-transform property does not seem to be supported.
Is there some list of the supported properties, and any ideas on how to get my text to be all upper case?
I have a font that only really looks good on upper case things and i want to use that, but now i cant :(

---

### Post by 1kivi on 2019-12-13
I've found a "fix" for my problem but there has to be a nicer way tho.
My fix is to use fontforge to create a font where the non capital letters are copies of the capital ones, and the use ttx (fonttools) to configure and rename the font install it and boom you have a new, all caps font and i used that, hope that helps if anyone needs somrthing like this.

---

