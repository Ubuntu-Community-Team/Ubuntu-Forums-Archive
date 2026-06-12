---
title: "Firefox misinterpretes comma as pipe in numpad"
date: 2005-02-08
forum: Desktop Environments
---

### Post by hashimoto on 2005-02-08
Gents,

It seems that Firefox is misinterpreting the comma in the number pad, at least for me. Instead of giving comma (,) it prints pipe (|). The comma on the alphabet side of the keyboard is OK, this happens only on the numpad part. I'm using finnish keyboard and all other apps are OK, it's just the Firefox. A bit annoying especially when doing my online banking.

Mandrake used to have the same bug earlier.I was told that Mozilla was not properly integrated with the KDE. Anyway, Mandrake got it sorted out later. Is this the same case, maybe? What can be done? Any help would be appreciated. Or should I report a bug?

Other finns on the list, do you have the same problem?

BR
Hashimoto

---

### Post by ow50 on 2005-02-08
[QUOTE=hashimoto]Other finns on the list, do you have the same problem?[/QUOTE]
Yes. Using firefox 1.0.

---

### Post by hashimoto on 2005-02-08
Sorry, forgot: Firefox 1.0 too on Hoary

Hashimoto

---

### Post by Yzka on 2005-02-08
Same problem, 1.0 in Warty.

---

### Post by hashimoto on 2005-02-08
I filed a bug report (no 6301). Lets hope this gets fixed.

Hashimoto

---

### Post by Werre on 2005-03-09
[QUOTE=hashimoto]
Other finns on the list, do you have the same problem?

BR
Hashimoto[/QUOTE]

I was having the exact same problem today but with another fellows SuSe 9.2 Pro distro. The problem does not exist on my debian unstable.

Seems that keymap sends KP_Separator keysym on the non-working SuSe, but it sends (correcly) KP_Decimal on the debian. Maybe there's a bug in finnish keymap. 

The fix:
xmodmap -e 'keycode  91 = KP_Decimal comma KP_Delete'

I've always used my own xmodmap and have no idea how keymaps are configured in X in a more modern way  8-)

---

### Post by hashimoto on 2005-03-22
This has been fixed a few days ago! Thanks!

---

