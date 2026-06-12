---
title: "Compiz &amp; Global Menu Alpha Transparency Effects"
date: 2012-05-23
forum: Desktop Environments
---

### Post by Bandit on 2012-05-23
Been slowly tweaking my UI. But having the darnedest time trying to get the Global menu's drop down menus to be transparent. I am using the Compiz Settings UI and got my dialogs and other programs to be transparent. But for the life of me I cant get the drop down menus to work anymore. I have tried type=Menu menu dropdownmenu DropDownMenu popupmenu and even GlobalMenu and globalmenu. Still no dice? Anyone know what its being referred to now? Google wasnt no help.

Thanks,
Joe

---

### Post by Bandit on 2012-05-24
:: Bump ::

Anyone?

---

### Post by jadtech on 2012-05-25
dont seem to be able to make any drop down menu transparent here at all most everything else no problem

---

### Post by zombifier25 on 2012-05-25
You meant the menu on Global Menu? I was able to make it transparent. Here's the rule I used in order to make ALL windows and menus transparent (copied from Animation plugin, ho ho ho):
```
(type=Menu | PopupMenu | DropdownMenu | Combo | Dialog | ModalDialog | Normal)
```

---

### Post by Bandit on 2012-05-25
> **zombifier25 said:**
> You meant the menu on Global Menu? I was able to make it transparent. Here's the rule I used in order to make ALL windows and menus transparent (copied from Animation plugin, ho ho ho):
```
(type=Menu | PopupMenu | DropdownMenu | Combo | Dialog | ModalDialog | Normal)
```

Hmm, let me try those again. Swore I tried every one there. This time I will add the whole list like you have it.

Thanks,
Joe



That got it working. I swore it tried every type on the list above. IDK.. Guess I am loosing my mind. Any way many thanks Z.  - Joe

---

### Post by cthom on 2012-05-27
where do i find this in ccsm? i've changed top panel transparency (although it seems to be on or off no matter the value). i'd like to alter menus too...

---

### Post by Frogs Hair on 2012-05-27
I followed this guide .[http://technostripe.com/make-menus-transparent-with-compiz/](http://technostripe.com/make-menus-transparent-with-compiz/)

---

### Post by cthom on 2012-05-27
done :mrgreen:

---

