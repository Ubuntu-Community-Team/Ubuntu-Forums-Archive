---
title: "[SOLVED] Why can't I &amp;quot;alt+tab&amp;quot;?"
date: 2007-09-07
forum: Desktop Effects &amp; Customization
---

### Post by staticvoid on 2007-09-07
Hi, I've messed around with effects and well... the wobbly windows just don't do it for me... The cube is nice, It get's a bit confusing. Anyway, it's all eye candy. When I uninstalled the effects and everything a few things happened

1. I lost my "alt+tab" switcher. I use this a ton
2. when I hit backspace in firefox it does not go back to the previous page, it just scrolls up a bit.
3. there is no three, Linux is wonderful

Hope someone can help! mainly with the alt tab thing. It must be in the "Configuration Editor" but I do not know how to use that thing. 

```

Sincerly,
Static Void 
```

---

### Post by Inxsible on 2007-09-07
so you are saying you have un-installed compiz fusion ?

anyway,

2 ) In firefox, you can go back to the previous page using Alt + Left keys. The backspace works in Opera.

---

### Post by praet on 2007-09-07
1. Check your system settings in the menu System > Preferences > Keyboard shortcuts : "Move between windows with popups".  Set that accelerator to Alt+Tab.

2. For this shortcut to work on Linux, use ```
about:config
``` to set the preference ```
browser.backspace_action to 0
```

3. Great.

---

### Post by staticvoid on 2007-09-07
Sweet, thanks praet, I'll try it out.

staticvoid

p.s. alt left...ok

---

### Post by staticvoid on 2007-09-08
Ok, so it worked! Great.
quick question, is there a way to have the cube as you ONLY effect? I...removed everything :( I tried compiz fusion, then removed that (before I installed that I removed ubuntus built in effects) then I tried beryl and removed that... So...I you just like to have the cube, it is auctually perty handy.

staticvoid

---

### Post by scxtt on 2007-09-08
you should be able to do it via gconf-editor:
```
/apps/compiz/general/allscreens/options/active_plugins
```

---

### Post by staticvoid on 2007-09-08
Ok, thank you.

Now: How do I edit this post so it says "[solved]"? Thank you all very very much :)!!

StaticVoid

---

### Post by staticvoid on 2007-09-08
nevermind....

---

