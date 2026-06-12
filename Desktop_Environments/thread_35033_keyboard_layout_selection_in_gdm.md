---
title: "keyboard layout selection in gdm?"
date: 2005-05-17
forum: Desktop Environments
---

### Post by Zed on 2005-05-17
Hi all,

I use the Dvorak keyboard layout, but my keyboard is labelled QWERTY. In general, this works great, but now I have a problem:

I'd like to give my wife a login on my machine. She doesn't know Dvorak, and given that the keyboard is QWERTY, she can't even hunt and peck.

I can set it up so she gets a QWERTY layout when she logs in, but I don't see a way to let her choose QWERTY at the login screen (without setting QWERTY globally for gdm, meaning I'd have to use it, too.)

Is there a way to get gdm to offer a keyboard layout menu like it offers a locale menu?

Thanks.

---

### Post by rrohde on 2007-08-27
Yep... our issue is very similar, as we provide 2 keyboard layouts in our environments which NEED to be available at GDM level. 

It's rather disheartening that there are so many users on this Ubuntu forum and there's yet no answer to this. 

Would be really nice if this could be done - having a dropdown box that allows a user to choose his/her keyboard layout to provide the username/password before logging in... :confused:

---

### Post by daveerickson on 2007-10-27
> **Zed said:**
> Hi all,

I use the Dvorak keyboard layout, but my keyboard is labelled QWERTY. In general, this works great, but now I have a problem:

I'd like to give my wife a login on my machine. She doesn't know Dvorak, and given that the keyboard is QWERTY, she can't even hunt and peck.

I can set it up so she gets a QWERTY layout when she logs in, but I don't see a way to let her choose QWERTY at the login screen (without setting QWERTY globally for gdm, meaning I'd have to use it, too.)

Is there a way to get gdm to offer a keyboard layout menu like it offers a locale menu?

Thanks.

Are you still having this issue. It is my exact issue as well, to a tee!

---

### Post by daveerickson on 2007-10-31
Bump.

---

### Post by daveerickson on 2007-11-03
Bump.

---

### Post by daveerickson on 2007-11-12
Bump.

---

### Post by daveerickson on 2007-12-01
Bump.

---

### Post by daveerickson on 2007-12-27
Bump.

---

### Post by der_joachim on 2007-12-27
There is a way to switch keyboard layouts on the fly, XP style, by hitting Alt+Shift. Here's how to configure it:

- Open /etc/X11/xorg.conf in your favourite text editor. Make sure you have root access!
- Find the keyboard subsection and replace  it with the following piece of code
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us(intl),us(dvorak)"
    Option         "XkbOptions" "grp:alt_shift_toggle"
EndSection

```
Please note that if you do nat care for accented characters, you have to use us(us) instead of us(intl)!
- Restart X and you should be set.

---

### Post by daveerickson on 2008-01-09
Well this is what my xorg looked like before:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"dvorak"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

This is what I changed it to, but it won't change:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
        Option          "XkbLayout" "us(us),us(dvorak)"
        Option          "XkbOptions" "grp:alt_shift_toggle"
EndSection

Thanks for the suggestion. Any other ideas?

---

### Post by Sef on 2008-01-10
Easy way to switch keyboard layout:

1) Right click on the top bar > Add to Panel > Search > Keyboard Indicator > Double click on keyboard indicator icon > Click on icon to change between QWERTY and Dvorak

---

### Post by mister_pink on 2008-01-10
Except you can't do that on the login screen ;) 

Exact same problem here, I tried editing my xorg.conf and nothing seems different. 

On another note, I sometimes tell other people that say "can I just use your computer to check my emails" that its difficult to change layouts, because watching as they struggle gives me a warm fuzzy feeling inside :D I think I might go back to my trackball too.... I'm not a sadist really! When will people learn the wonder of dvorak though!

---

### Post by der_joachim on 2008-01-11
Hmmm.. Strange. No problems here. I copied and pasted from my xorg.conf, so no typos. I can think of two things, but I suspect that neither is the case:

1) In KDM, you never see a keyboard layout indicator. You do switch though, although invisibly. However, I assume people have tried typing stuff anyway, so they would have known whether it would have worked.
2) I sometimes notice a slight delay (0.5 seconds-ish) when using Alt+Shift in KDM. I have a fast PC, so hardware is not the issue. Maybe you simply typed too fast. Happens to me all the time. 

Hope this helps. :confused:

---

### Post by daveerickson on 2008-01-27
Bump.

---

