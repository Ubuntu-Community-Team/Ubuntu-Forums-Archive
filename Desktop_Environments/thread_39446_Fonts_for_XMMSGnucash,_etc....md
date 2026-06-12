---
title: "Fonts for XMMS/Gnucash, etc..."
date: 2005-06-05
forum: Desktop Environments
---

### Post by Nequeo on 2005-06-05
Greetings,

I've noticed a few different programs seem to share a font that can't be controlled through the Font section of preferences.

Specifically, Gnucash and XMMS are the ones I have noticed, but no doubt there are more. Unfortunately, on my cheap LCD, that font looks absolutely horrendous. All distorted and squiggly, almost unreadable.

I don't seem to recall having the same problem on CRTs or the expensive LCDs at work. 

I've tried fiddling around with different themes, and even KDE, but I can't seem to find a way of changing that font to something more readable.

Any hints, please?

Cheers,

---

### Post by xristos on 2005-06-05
For XMMS look for a config file in .xmms folder which should be located in your home folder .

---

### Post by mrsad on 2005-06-05
That is because those are old GTK 1.x programs, they have their own config and do not follow the settings you use for GTK 2.x, you can still change it ofcourse, for that you need to edit a file called '.gtkrc.mine' in your home (it will not be there by default though).

---

### Post by Nequeo on 2005-06-05
Aha! Thanks, both. That was exactly what I needed to know. 

Cheers!

---

### Post by jonny on 2005-06-06
OK.  I've googled around and sussed that I need to create a file called ~/.gtkrc.mine, and I need to put this into it:
```
style "user-font"
{
  fontset="-monotype-arial-medium-r-normal-*-14-*-*-*-p-*-iso8859-1"
}
widget_class "*" style "user-font"
```Is there any way I can pretty things up further  by having anti-aliasing for GTK 1.x applications?

---

### Post by Alexander Kirillov on 2005-06-06
[QUOTE=jonny]OK.  I've googled around and sussed that I need to create a file called ~/.gtkrc.mine, and I need to put this into it:
```
style "user-font"
{
  fontset="-monotype-arial-medium-r-normal-*-14-*-*-*-p-*-iso8859-1"
}
widget_class "*" style "user-font"
```Is there any way I can pretty things up further  by having anti-aliasing for GTK 1.x applications?[/QUOTE]

Antialiasing - no. At least, not in any easy way - this was one of reasons for gtk1 ->gtk2 change. 

Also: the font choice you show can cause problems for non-ascii  (such as accented leeters, or non-latin symbols) symbols: by default, Hoary uses utf8 encoding, not iso8859-1. Of course, ascii parts of these coincide. 

For proper handling of utf8 in gtk1 apps, see here
[http://ubuntuforums.org/showthread.php?t=39218](http://ubuntuforums.org/showthread.php?t=39218)

---

