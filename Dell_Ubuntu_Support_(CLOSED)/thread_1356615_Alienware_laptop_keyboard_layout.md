---
title: "Alienware laptop keyboard layout"
date: 2009-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by georgestan on 2009-12-16
This case has been solved.

Hello,

I installed Ubuntu Karmic on my Alienware m15x. All work well, but there is a little bit annoying with the keyboard.

When I use a terminal program such as less, I press / to search for text. After entering the match string, I press the enter key to let it go, only to get "ESCOM" (ESC, O, M actually). I read somewhere else that this is due to enter and return are not considered to be the same.

When I use an external keyboard (the standard one with numberic pad), this is not a problem.

Is there anyway to change the keymapping to get ENTER work in terminal? The only affected program so far is less.

Regards,

---

### Post by georgestan on 2010-01-06
There is a workaround.

The reason is that Linux treats Enter and Return differently. Alienware m15x has only an Enter key.

Run xev to find that Enter key correspond to keycode 104.

Use xmodmap -e 'keycode 104 = Return' to merge Enter and Return together.

---

### Post by AndersAA on 2010-01-14
This is actually a bios bug fixed in A03 (which has been pulled back because it's known to brick computers).

If you have numpad on it'll register as enter, otherwise it'll register as keypad enter, which is obviously the wrong way around.

---

