---
title: "xfce mouseclick simulation (using xte) with keyboard keys doesnt work 100%"
date: 2012-02-03
forum: Desktop Environments
---

### Post by engineerelektro on 2012-02-03
Hi all,

I would like to set some of my laptop keys to simulate mousekey clicks as follows:

F1 = click left mb once
F2 = click left mb double
F3 = click right mb once

(I did the same setup in Windows by using the autohotkey software.)

To realise this, here is what I did:

Run command ```
xfce4-keyboard-settings
``` and add 3 shortcut keys: F1, F2, F3. The commands to execute on these respective keys are as follows:

F1 = xte 'mouseclick 1'
F2 = xte 'mouseclick 1' 'mouseclick 1'
F3 = xte 'mouseclick 3'

However, this seems to work only partially. The reaction of mouseclicks is not always as expected (not similar as when i click on the real mouse buttons). For example, within firefox it works like a charm, but when i click on the XFCE menubar in top of my window, for example the little mouse logo top left to open the programs menu, it does not react.

When i have a terminal open and i want to left click on the file menu, it does not open the file menu. 

I would like to know if anyone else has:
- some clues about what the cause of this could be?
- done a similar setup in another way, which works 100% as expected?

Would be really nice to fix this 

Tnx!

---

### Post by quadra on 2012-07-10
Hi

Same problem here, with Xubuntu 12.04. It also happens with keyboard shortcuts. Hope someone can help us?

---

### Post by quadra on 2012-07-10
It seems as if "focus was stolen" from the window while we press the shortcut key. As a temporary and **ugly** workaround, I use a small delay to generate the sequence only after we release the key; in my case, around 80'0000 microseconds.

Example to close a window (Alt+F4):

```
xte 'usleep 80000' 'keydown Alt_L' 'key F4' 'keyup Alt_L'
```

---

