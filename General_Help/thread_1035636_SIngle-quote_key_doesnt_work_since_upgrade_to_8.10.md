---
title: "SIngle-quote key doesnt work since upgrade to 8.10"
date: 2009-01-09
forum: General Help
---

### Post by skewray on 2009-01-09
I recently upgraded to 8.10.  When I am typing in a konsole window with csh, I cannot type the single-quote character.  If I switch to sh, I can get a single-quote by typing it twice.  In konqueror, I can get one by typing twice as well.  Same with xterm.  How do I make this weird behaviour go away?  Thanks!

Brian

ps -- Double quotes (same key but shifted) has the same irrational behaviour.

pps - So does the hat character (^).

ppps - Same if I go into single-user non-graphics mode with cntl-alt-F2 and try to type in a login.

---

### Post by ajmorris on 2009-01-10
hi there,
this behaviour is caused by using the 'us_alt' keyboard layout, instead of just 'us'
To change it to 'us' layout, just go to:
Preferences -> Keyboard -> Layout
and select us.


AJ

---

### Post by skewray on 2009-01-10
> **ajmorris said:**
> hi there,
this behaviour is caused by using the 'us_alt' keyboard layout, instead of just 'us'
To change it to 'us' layout, just go to:
Preferences -> Keyboard -> Layout
and select us.


AJ

Hi!  I think you gave me a vital clue as to what is wrong, but I still dont understand how to fix it.  In KDE 4 I have <System Settings> in the main menu, but the keyboard choice leads to a form with no reference to layout.  How do I get the <Preferences> you refer to?  Thanks!

Brian

---

### Post by ajmorris on 2009-01-11
> **skewray said:**
> Hi!  I think you gave me a vital clue as to what is wrong, but I still dont understand how to fix it.  In KDE 4 I have <System Settings> in the main menu, but the keyboard choice leads to a form with no reference to layout.  How do I get the <Preferences> you refer to?  Thanks!

Brian

haha, sorry, i assumed you were using gnome (didn't notice the [kubuntu] tag) :P In KDE, go to your system settings manager, then to Peripherals -> keyboard


AJ

---

### Post by skewray on 2009-01-11
<System Settings> has no <Preferences>.  The keyboard settings seem to be split into either <Keyboard & Mouse> or <Region & Language>, but I still cant find anything related to us_alt.  The closest seems to be some bits related to the X keyboard settings, but the problem I have persists even when not using X.

Brian

---

### Post by ajmorris on 2009-01-12
odd that you couldn't find the option in the kde keyboard settings... there should be a layout option there somewhere... However, i didn't realise that your problem was not just in Xorg. You might like to see what the ```
XKBLAYOUT=""
``` option is set to in /etc/default/console-setup  -- it should be set to us.


AJ

---

### Post by skewray on 2009-01-16
Here is my /etc/default/console-setup file:
```

BOOTTIME_KMAP_MD5="90e19b1026bc78397e430bedc86983a4"
ACTIVE_CONSOLES="/dev/tty[1-6]"
CHARMAP="UTF-8"
CODESET="Lat15"
FONTFACE="VGA"
FONTSIZE="16"
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="intl"
XKBOPTIONS="lv3:ralt_switch"

```

Any insights?

Brian

---

### Post by elfgoh on 2009-01-20
> **skewray said:**
> Here is my /etc/default/console-setup file:
```

BOOTTIME_KMAP_MD5="90e19b1026bc78397e430bedc86983a4"
ACTIVE_CONSOLES="/dev/tty[1-6]"
CHARMAP="UTF-8"
CODESET="Lat15"
FONTFACE="VGA"
FONTSIZE="16"
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="intl"
XKBOPTIONS="lv3:ralt_switch"

```

Any insights?

Brian

Comment out 

XKBVARIANT="intl"

---

### Post by skewray on 2009-01-24
Problem solved!  Thanks!

---

