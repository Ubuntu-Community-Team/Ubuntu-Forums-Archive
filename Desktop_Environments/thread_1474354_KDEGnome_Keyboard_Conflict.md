---
title: "KDE/Gnome Keyboard Conflict?"
date: 2010-05-06
forum: Desktop Environments
---

### Post by czheng on 2010-05-06
Hey all,

Just did a fresh install of Kubuntu 10.04. I use Gedit as my primary text editor. When I was running 9.10, I was able to map shortcuts in Gedit for code snippets and use them without any problems.

Now, in 10.04, when I map shortcuts in Gedit, as expected my WIN key is recognized as SUPER (which is how it was in 9.10). But for some reason, KDE now has that key mapped as META. Which means I can set the correct shortcut in Gedit, but can't ever use it because KDE seems to think there is no SUPER key.

I've tried every conceivable option in System Settings > Regional & Language > Keyboard Layout > Advanced > Alt/Win Key Behavior. Nothing works. I've also tried various combinations of enabling/disabling keyboard layouts altogether, and switching keyboard models. No luck so far...

What's so mind-boggling is that this all worked flawlessly in 9.10. I must've screwed something up recently, but I have no idea where to look...

Any guidance or pointers would be greatly appreciated. Thanks :)

---

### Post by czheng on 2010-05-06
So running xev, I see that the WIN key is indeed recognized as SUPER_L... But if I try to use it to assign keyboard shortcuts in KDE, it is interpreted as META. So, if I understand correctly, somehow KDE is changing the mapping from SUPER_L to META.

---

### Post by AlejandroDelLoco on 2010-05-11
I am having a similar problem in Gnome - xev shows that my keypresses on SUPER_L are being recognized, but when I try to use the key in gnome (for instance, trying to assign a hotkey), it doesn't register at all.

HALP

---

### Post by AlejandroDelLoco on 2010-05-11
Oh *weird* - it seems that in system>preferences>keyboard>layouts the way to map super to win is pretty counterintuitive!

Under "Alt/Win Behavior" you have to say "Add the standard behavior to Menu Key" instead of "Default" (for the record, I also have compose on the menu key).

Why the hell did they change that? Just to confuse me? In Karmic and before there was a more overt option to map super to the win key. Harumph.

---

### Post by czheng on 2010-05-13
Hm. What sucks is that I'm on Kubuntu so my preferences are different. Is there a Gnome preferences file where those changes get written that you could share?

---

### Post by AlejandroDelLoco on 2010-05-13
Actually it seems that this didn't stick. In fact, I think I messed around with stuff so much that my problem got weirder. Now, when I run xev, I get this when I press the left windows key:

```
KeyRelease event, serial 36, synthetic NO, window 0x6e00001,
    root 0x99, subw 0x0, time 12380119, (-415,-510), root:(524,74),
    state 0x0, **keycode 133 (keysym 0xff20, Multi_key)**, same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

It used to be Super_L, not Multi_key.

Oy.

EDIT: I fixed it. I just had to change my xmodmap so it had the following:

```
keycode 133 = Super_L NoSymbol Super_L
```

---

