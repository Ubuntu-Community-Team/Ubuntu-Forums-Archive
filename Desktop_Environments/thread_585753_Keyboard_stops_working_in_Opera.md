---
title: "Keyboard stops working in Opera"
date: 2007-10-21
forum: Desktop Environments
---

### Post by jetthe on 2007-10-21
After using Opera ~5 minutes the keyboard stops working. Neither shortcuts (ctrl+v, ctrl+tab, etc) or typing in the address bar works. Everything else works though, mouse gestures and clicking links, etc. The keyboard continues to work perfectly outside Opera.

Opera versions: Both 9.24 and 9.50 (build 1636)
QT: .6_shared.
Distribution: Ubuntu (7.10)

Using "opera -debugkeyboard -debugxerrors" all pressed keys are shown until suddenly, it doesn't register the keys anymore. No error messages or such.

```
Qt  keypress: key: C (0067), ascii: c (099), state: 00000000
X11 keypress: window=03e008fd, state=00000010, keycode=00000020, keysym=0000006f ('o'), focus: QWidget, context: Edit Widget
Qt  keypress: key: O (0079), ascii: o (111), state: 00000000
X11 keypress: window=03e008fd, state=00000010, keycode=0000003a, keysym=0000006d ('m'), focus: QWidget, context: Edit Widget
Qt  keypress: key: M (0077), ascii: m (109), state: 00000000
```

The problem appeared after upgrading from Ubuntu 7.04 (Feisty) to 7.10 (Gutsy) so it's probably distro-related. Any help on fixing it is appreciated!


Edit: This thread should probably been been posted in "General Help", feel free to move it.

Edit2:  The same thing also happens in aMSN.

Edit3: When using the static QT version of Opera the keyboard works flawlessly in Opera, but not at all in content provided by the flash plugin.

---

### Post by coconutstudio on 2007-11-15
Me, too.  On Gutsy, It would work for awhile and then suddenly all the keyboard input just stops in Opera.

---

### Post by LazarusHC on 2007-11-16
I'm having the same problem.  It also happened in Firefox, once -- while my wife was typing an e-mail, no less.  I want to fix this before I hear, "This never happened in Windows."

---

### Post by solanum on 2008-04-11
I don't suppose a fix was ever found for this.
I'm using Ubuntu 8.04 and Opera 9.27, and I'm having that same problem.
I find that if I minimize and the restore opera, it'll work for a short while again.

---

### Post by yang on 2008-04-27
Bump.  I just upgraded from 7.10 to 8.04 and am now experiencing the same problem (never had a problem in 7.10).  I'd been using 9.50b1.  I tried out 9.50b2, but the problem pesists.

---

### Post by malagigi on 2008-05-19
Something of note that I just observed in relation to this issue:
I just installed Ubuntu 8.04, and shortly there after installed Opera 9.27.  This morning, when I typed in the address bar the keyboard seemed to stop working, only after I type a period (as in www**.**).  After turring off support for complex characters in language support the problem seems to have gone away.  

Obviously, it would be nice to have both complex characters and Opera.

---

