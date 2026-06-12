---
title: "How do I fix this?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by ardchoille on 2006-07-22
On my keyboard, I have SPACE | ALT | WINDOWS KEY | MENU KEY | Ctrl along the bottom right area. The menu key looks like a menu with an arrow on it. I accidentally hit this key a lot when I am trying to hit the right shift key and I have to hit Esc to get rid of the popup it causes. I think I can remap this key to something different, but I need to know two things:

1) How do I find the signal that this key sends
2) How do I map it to a new function (possibly the same as a SHIFT KEY function)

Any ideas?

---

### Post by jordilin on 2006-07-22
System->Preferences->Shortcuts

---

### Post by ardchoille on 2006-07-22
> **jordilin said:**
> System->Preferences->Shortcuts

Unless I am missing something, there is no way to disable that particular key in System->Preferences->Shortcuts. Can you teach me what you are trying to say?

---

### Post by Ben Armston on 2006-07-22
I dont' know precisely how to acheive this, but you should find the information in ```
man keymaps
``` or one of the man pages at the bottom of that page. If you find out the command, please post back for my own curiosity. ;) 

Ben.

---

### Post by ardchoille on 2006-07-22
I am not understanding any of this cryptic stuff. It would be nice if this stuff was printed in plain English.. or if someone could just give me the command to disable that paticular key. I don't have 6 months to consult 50 dictionaries and websites just to sort out what these man pages are saying.

---

### Post by ardchoille on 2006-07-22
Solved this problem:

Open a term and run xev. xev will output any and all actions on the computer. I pressed the Menu key while xev was running and found this:

```

KeyPress event, serial 32, synthetic NO, window 0x2200001,
    root 0x4c, subw 0x0, time 2567483792, (249,49), root:(752,309),
    state 0x10, keycode 117 (keysym 0xff67, Menu), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x2200001,
    root 0x4c, subw 0x0, time 2567483818, (249,49), root:(752,309),
    state 0x10, keycode 117 (keysym 0xff67, Menu), same_screen YES,
    XLookupString gives 0 bytes:

```
This told me the keysym I needed to fix the problem. Then I took that keysym (Menu) and used it in a xmodmap command:

```

sudo xmodmap -e "keysym Menu = "

```
which effectively maps the Menu key to nothing. I tried the menu key and it indeed does nothing now. Problem solved :)

---

### Post by Mach1US on 2006-09-10
Does anybody know how to make those changes to key mapping permanent?

---

