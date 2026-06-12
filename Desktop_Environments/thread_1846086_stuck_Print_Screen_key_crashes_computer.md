---
title: "stuck Print Screen key crashes computer"
date: 2011-09-18
forum: Desktop Environments
---

### Post by bsmith1051 on 2011-09-18
I have this ongoing problem wherein my kids will shove the keyboard tray back under the desk, pinning the keyboard.  The way the bracket is positioned, the Print Screen button gets stuck.  When I go to use the computer I'll find hundreds(?) of Print Screen prompts on-screen, the hard-drive light lit-up solid, and the computer totally locked-up.  I've wasted lots of time trying to recover without resetting but I always give-up eventually and pull the plug.  (Even ALT-F1 fails to respond.)

Any suggestions on fixing or avoiding this?  Besides removing my keyboard tray?
_____________

Does this count as a bug?
Can I disable the Print Screen function?

---

### Post by Krytarik on 2011-09-18
Nope, obviously no bug, but user error. :p

For simply disabling the Print key, create a file called ".Xmodmap" in your home directory with the following content:

~/.Xmodmap:
```
keycode 107 = NoSymbol Sys_Req NoSymbol Sys_Req
```The next time you log in, you will most probably be asked if you want to use those keymap file*, then just choose "Add" and confirm with "OK". It should work then.

Greetings.

*depends on if you had such a file before, and did already confirm/disable those query

---

### Post by bsmith1051 on 2011-09-18
I wasn't implying my keyboard tray constituted a bug :-)  I was wondering if the OS should be able to tolerate a 'stuck' key without crashing.

What about reprogramming the Keyboard Shortcut for Desktop > Take A Screenshot?  I changed that from 'Print' to 'Ctrl+Print' and now the PrtScrn button doesn't seem to do anything on it's own.  So this might be an effective workaround?

---

### Post by Krytarik on 2011-09-18
> **bsmith1051 said:**
> What about reprogramming the Keyboard Shortcut for Desktop > Take A Screenshot?  I changed that from 'Print' to 'Ctrl+Print' and now the PrtScrn button doesn't seem to do anything on it's own.  So this might be an effective workaround?
Yeah, this is another workaround, indeed. Since the key doesn't invoke the hundreds of 'Take Screenshot' windows anymore, you might be well off with this.

Reg. my initial suggestion, however, it's possible to preserve the SysRq feature, just didn't think of that. I'll update my initial reply in that regard.

---

