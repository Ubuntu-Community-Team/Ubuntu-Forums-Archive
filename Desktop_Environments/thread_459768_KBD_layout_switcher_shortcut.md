---
title: "KBD layout switcher shortcut"
date: 2007-05-31
forum: Desktop Environments
---

### Post by weboholic on 2007-05-31
Hello,

using Feisty I've added the KBD layout applet to the panel. But I can't find where and/or how to define a shortcut for easily switching between the layouts (I have 3 layouts).

It is great that different windows can remember their own KBD layout state, but different tabs in FF can't. And as KBD user I find it most annoying to always have to grab the mouse move it up click once or twice and than focus once again the textarea by clicking in it.

Thank you in advance.

---

### Post by weboholic on 2007-06-06
Hi, once again.

I am definitely not a bumper, but I've kinda feel like one right now ... I feel like I am forced to bump, even if just to get a answer like "hey, this is not possible".

I will be happy with that, because, I would know - it is not possible.

Aren't there any multilingual ubuntu users with this problem?

---

### Post by der_joachim on 2007-06-07
Are you a KDE user? I can at least offer you a partial solution. Here's my situation: I recently switched to Dvorak. My wife still uses US. X starts  with US layout as default, but I can switch to Dvorak on the fly by pressing Alt+Shift. 

When I log into my own account though, the default layout is Dvorak, but I can fall back to US by clicking the keyboard applet icon in the taskbar. I disabled Alt+Click on purpose, since it would interfere with other shortcuts.

To configure X, you should open /etc/X11/xorg.conf and edit the keyboard section like this:
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us(intl),us(dvorak)" ## <-- Put your layouts here!
    Option         "XkbOptions" "grp:alt_shift_toggle" ##<-- Enables Alt+Shift
EndSection

```

If you use KDE, here's how to configure different layouts:
- Open System settings
- Click Regional & Language and select Keyboard layout.
- Add and remove layouts as desired.
- Click on the tab 'Switching options' and select your desired switching policy. You can also configure your tray applet to look like a little flag, which may be useful for you.
- In the tab 'Xkb Options' you can configure your keyboard even more.

Hope this helps. Good luck!

---

### Post by weboholic on 2007-06-12
Hey, thanks for the reply. I am on GNOME ( feisty, right? :) )

However I once again tried the preference of the KBD switcher applet and guess what - I found it; It isn't called something like "%layout switcher%" but "**Group Shift/Lock behavior**", so setting it to "alt+shift" (a windows shortcut) solved this issue.

---

### Post by Spr0k3t on 2007-06-12
Awesome... been looking for this one for quite some time while I made the switch over to dvorak...

---

