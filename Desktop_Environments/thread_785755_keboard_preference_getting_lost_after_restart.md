---
title: "keboard preference getting lost after restart"
date: 2008-05-07
forum: Desktop Environments
---

### Post by jaskah on 2008-05-07
hello
i just upgraded to hardy heron on my lenovo t61 laptop.
everything is working basically ok, with the exception that my keyboard preferences are getting lost after re-starting the computer.
in system/preferences/keboard/layout/layout options/third level indicators i am checking the box for "press any alt keys to choose 3rd level."
i am using the alt keys to access letters for german (ü, ö etc).
i am using keyboard layout us international (alt gr dead keys).
after re-starting these keys no longer work and i have to configure everything again.
any help on this will be greatly appreciated!

---

### Post by jaskah on 2008-05-09
can anyone help me on this?
thanks.

---

### Post by emacs on 2008-05-13
> **jaskah said:**
> can anyone help me on this?
thanks.

I don't have an answer for you, but 
I would like to report a similar problem on my HP DV6000 laptop.  I
upgraded (an upgrade rather than reinstall) from ubuntu 7.10 to 8.04 a
few days ago.  Since then I have several problems one of which is
keyboard preferences not working right.

I checked the "Make CapsLock an additional Ctrl" option under
System->Preferences->Keyboard->Layouts->Layout Options->Ctrl key position.
This makes the CAPS LOCK key work as another Control key as documented.
However rebooting returns the key back to its caps-lock function.  If
I bring up the keyboard preferences GUI, the checkbox is still
checked!  At this point if I select Default option, then back to "Make
CapsLock an additional Ctrl", then the CAPS LOCK key works as another
Control.  So I have to bring up the Keyboard GUI each time I boot in
order to change the keyboard setting!  I did not have to do this with
7.10.

I should also add that the small blue LED next to the CAPS LOCK key
toggles between off-state and on-state each time the CAPS LOCK key is
pressed even when it is functioning as another Control key.

I use HP DV6000 laptop connected to HP xb3000 Notebook Expansion Base if this matters.  The same setup worked fine with 7.10.

In case it matters, the USB keyboard and mouse stops functioning altogether if the computer is suspended then resumed.  I have to
reboot in order for the USB keyboard/mouse to work at this point.
Again I did not have this problem with 7.10.

---

### Post by nimbostratus on 2008-05-13
I'm getting a similar problem with using a UK layout keyboard. Started happening on upgrade from Gutsy to Hardy.

The UK layout works fine when set in the 'Keyboard Preferences' dialog, but stops after reboot. And yes, the settings are still present in the dialog even after they've stopped working.

Interestingly, I've placed the layout switcher on the panel just to see what happens. Again, it works when preferences are set, but after reboot it still appears to switch between US and UK, but actually has no effect.

I have a suspicion this can be fixed in xorg.conf - an old version of my file mentions the proper layout, but the current version doesn't. Will report how that goes.

---

### Post by nimbostratus on 2008-05-13
This has been reported as a bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/196277]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/196277")

Two solutions worked for me:

1) Disable automatic/timed logon.
It seems the gnome settings aren't properly applied at automatic logon.

OR

2) Edit xorg.conf (I can advise how to do this if you need me to, or I'm sure there are other posts that can help :))

In my case, I changed the following:

```
Section "InputDevice"
  Identifier "Generic Keyboard"
  ......
  Option "XkbLayout" "us"
EndSection
```

by entering "gb" in place of "us".

In jaskah and emacs cases, there are other Options for what you need to change, but I don't know what they are (Maybe some of the info in the bug report above could help?). I had a file xorg.conf.1 in the same directory as xorg.conf that I copied from. I think this is a backup of your old Gutsy configuration.

Hope this helps, please ask if you need any further explanation.

---

### Post by unutbu on 2008-05-13
jaskah, after you use System>Preferences>Keyboard to set your keyboard layout, open a terminal and type

```
xprop -root | grep XKB
```

You might see something like this:

```
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "basic", "ctrl:nocaps"
_XKB_RULES_NAMES(STRING) = **"xorg", "pc105", "us", "alt-intl", "ctrl:nocaps"**
```

The line that begins with "_XKB_RULES_NAMES(STRING) = " ends with a list of 5 strings. Those strings correspond to XkbRules, XkbModel, XkbLayout, XkbVariant, XkbOptions.

Now run

```
gksudo gedit /etc/X11/xorg.conf
```

Find the stanza that looks something like this, and edit the XkbRules, XkbModel, XkbLayout, XkbVariant, XkbOptions lines to match the info you obtained from the `xprop -root | grep XKB` command above.

```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" **"xorg"**
    Option         "XkbModel" **"pc105"**
    Option         "XkbLayout" **"us"**
    Option         "XkbVariant" **"alt-intl"**
    Option         "XkbOptions" **"ctrl:nocaps"**
EndSection

```
emacs, the     
```

Option         "XkbOptions" "ctrl:nocaps" 
```

line is what you need to turn your capslock into a control key.

---

### Post by jaskah on 2008-05-19
hi 
thanks for all your answers.
for me, the easiest workaround at this point was to just disable automatic login.
jaskah

---

### Post by binary.koala on 2008-10-10
thanks!

> **unutbu said:**
> jaskah, after you use System>Preferences>Keyboard to set your keyboard layout, open a terminal and type

```
xprop -root | grep XKB
```

You might see something like this:

```
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "basic", "ctrl:nocaps"
_XKB_RULES_NAMES(STRING) = **"xorg", "pc105", "us", "alt-intl", "ctrl:nocaps"**
```

The line that begins with "_XKB_RULES_NAMES(STRING) = " ends with a list of 5 strings. Those strings correspond to XkbRules, XkbModel, XkbLayout, XkbVariant, XkbOptions.

Now run

```
gksudo gedit /etc/X11/xorg.conf
```

Find the stanza that looks something like this, and edit the XkbRules, XkbModel, XkbLayout, XkbVariant, XkbOptions lines to match the info you obtained from the `xprop -root | grep XKB` command above.

```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" **"xorg"**
    Option         "XkbModel" **"pc105"**
    Option         "XkbLayout" **"us"**
    Option         "XkbVariant" **"alt-intl"**
    Option         "XkbOptions" **"ctrl:nocaps"**
EndSection

```
emacs, the     
```

Option         "XkbOptions" "ctrl:nocaps" 
```

line is what you need to turn your capslock into a control key.

---

