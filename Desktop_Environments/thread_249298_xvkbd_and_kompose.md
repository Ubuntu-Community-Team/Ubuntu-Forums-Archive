---
title: "xvkbd and kompose"
date: 2006-09-02
forum: Desktop Environments
---

### Post by The Doc on 2006-09-02
So here is the situation:

I want to map the 10th mouse button of my MX1000 to show kompose. Which should be - in theory - very easy.

I set up kompose to use the global shortcut "Alt + Shift + W".
If I hit that combo on my keyboard it works like a charm. If I use xvkbd however (which I need for xbindkeys) chaos comes up:

`xvkbd -text "\AW"`

Kompose shows up and than the screen goes gray and I see that my pc is working pretty hard. The solution is to wait and keep pressing escape to eventually kill kompose. (Be warned: if you try that, your whole pc can crash as mine did a lot of times)

I don't know what's happening, I tried to use the newest version of xvkbd (2.7a something) but that doesn't work either. Look here for a konsole output after killing kompose with esc:
[http://ubuntu.pastebin.com/782058](http://ubuntu.pastebin.com/782058)

It keeps destroying the children and starting all over again.


Does anyone has a clue what I could do? Skippy doesn't work too, but thinks like katapult do work. Are there any alternatives? Do you use a mousebutton to do something like that? What did you do?

Maybe someone could test what I did to ensure that it is a bug and not something which I and my PC screw up.

Thanks!

Edit:
I could solve the problem by using Dcop. Use the following two lines in your .xbindkeysrc:

```
"dcop kompose KomposeDcopIface createDefaultView"
  b:10
```

---

