---
title: "\ key not working"
date: 2005-10-26
forum: Desktop Environments
---

### Post by Gtaylor on 2005-10-26
I'm currently complete unable to use my backslash key or the pipe with shift. At bootup I can but as soon as I'm sitting at my login prompt, I can't. Nothing happens when I hit the key, no X events are generated. I've tried different keyboards with the same result.

Switching to a tty, I still can't use it. Earlier in the bootup process I could though, I'm not sure what's breaking it. Any ideas?

---

### Post by David Marrs on 2005-10-26
I would guess that your keyboard layout is different from the locale you've specified during install. For example, if you use a US keyboard but specify a UK layout then you can have problems.

---

### Post by Gtaylor on 2005-10-26
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

I've got that covered already

---

