---
title: "Keybinding Right-ctrl key"
date: 2009-02-01
forum: General Help
---

### Post by CaptSpify on 2009-02-01
Is it possible to keybind the Right-CTRL key?
I've gotten to the Configuration Editor to change keys, but I can't seem to tie it to that specific key.

Any help?

---

### Post by SteveDee on 2009-02-01
> **CaptSpify said:**
> Is it possible to keybind the Right-CTRL key?
I've gotten to the Configuration Editor to change keys, but I can't seem to tie it to that specific key.

Any help?

I don't think it is because the 2 <ctrl> keys are treated the same, even if you are writing software to react to these keys being pressed.

Presumably (if these 2 keys are not wired together within the keyboard) if you were prepared to write your own keyboard driver, you could keep them separate.

---

### Post by boof1988 on 2009-02-01
> **SteveDee said:**
> I don't think it is because the 2 <ctrl> keys are treated the same, even if you are writing software to react to these keys being pressed.

Presumably (if these 2 keys are not wired together within the keyboard) if you were prepared to write your own keyboard driver, you could keep them separate.

I don't know how it works... but I believe they are separate.  When using VirtualBox (on my install) the default mouse-capture toggle is the <right-control>.  This caused me much frustration when I first tried VirtualBox because my keyboard (at the time) didn't have a <right-control>.

---

### Post by SteveDee on 2009-02-01
> **boof1988 said:**
> I don't know how it works... but I believe they are separate.  When using VirtualBox (on my install) the default mouse-capture toggle is the <right-control>.  This caused me much frustration when I first tried VirtualBox because my keyboard (at the time) didn't have a <right-control>.

Yes, you are right, they are wired separately. I just tried reading the Key.Code in Gambas and I get; 65507 for left <ctrl> and 65508 for right <ctrl>.

In System > Preferences > Keyboard > Layout > Options you can set left & Right <ctrl> options, but this does not seem to help when you go back to Keyboard Shortcuts, where left & right <ctrl> seem to be interpreted as the same key.

---

### Post by CaptSpify on 2009-02-02
Yeah, so I know they are interpreted differently on *some* level, I just can't figure out how to do it in gconf-editor's keybindings.

:(

---

### Post by CaptSpify on 2009-02-12
Bump

---

