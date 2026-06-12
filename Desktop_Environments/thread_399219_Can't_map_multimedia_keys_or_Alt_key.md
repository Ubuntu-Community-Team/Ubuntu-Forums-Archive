---
title: "Can't map multimedia keys or Alt key"
date: 2007-04-02
forum: Desktop Environments
---

### Post by se2131 on 2007-04-02
I have a Toshiba Satellite A75 series, and it has multimedia keys (play/pause, stop, ffwd, rewind, start) which do not register at all in the "xev" program (everything else does).  Is there any way that I can get them to do something useful?

Also, I can't seem to map the right Alt key to perform as it should.  When I run xmodmap -pke, I get...

...
keycode 64 = Alt_L Meta_L
...
keycode 113 = ISO_Level3_Shift
...

So then I tried remapping it using the following commands (one-by-one).  None of them worked:

xmodmap -e "keycode 113 = Alt_R Meta_R"
xmodmap -e "keycode 113 = Alt_R"
xmodmap -e "keycode 113 = Alt_L Meta_L"
xmodmap -e "keycode 113 = Alt_L"

However, if I do the following:

xmodmap -e "keycode 113 = a A"

then it acts like the "a" key properly.  My other Alt key works fine, so why can't I get this one to work?

Thanks in advance.

---

### Post by se2131 on 2007-04-03
Any ideas?

---

### Post by domino1241 on 2008-03-03
Hopefully this helps:

System->Preferences->Keyboard->Layout Options->Alt/Win behavior->Alt and Meta are on the same Alt keys (default)

[http://blog.andrewbeacock.com/2007/06/getting-right-alt-key-alt-gr-to-work-in.html](http://blog.andrewbeacock.com/2007/06/getting-right-alt-key-alt-gr-to-work-in.html)

---

