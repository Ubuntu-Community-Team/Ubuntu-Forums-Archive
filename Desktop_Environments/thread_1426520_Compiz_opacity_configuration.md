---
title: "Compiz opacity configuration"
date: 2010-03-10
forum: Desktop Environments
---

### Post by Obontoo on 2010-03-10
In compiz config (opacity, brightness and saturation) , I have window value set at 80 for "any" windows. This gives all windows opacity. However, I don't want the panels to have opacity.

I want all windows except the panel to have opacity. What code do I write under "Windows" which will affect all windows except the panels?

Thanks
/Obontoo

---

### Post by Tikkyca on 2010-03-10
Dont know how to help you,but to have transparent windows decoration use emerald,and you cand download some themes from gnome-look.com,to use emerald you need to get it from synaptic package menager,after you install it get some themes,install them,open up compiz settings mennager,go to effects,then to window decoration,after that is done backup code that is in command text form,and delete it,now tipe this:"emerald --replace"without the ".
Once you done that restart your pc,and you will see window decoration that you installed in emerald,to get back to normal decorator,just delet everything in command text form,and put the backup text there,restart your pc ;)

---

### Post by Obontoo on 2010-03-10
I already have emerald, I'm not talking about window borders but actual window opacity which is configured in compiz...

---

### Post by Tikkyca on 2010-03-10
> **Obontoo said:**
> I already have emerald, I'm not talking about window borders but actual window opacity which is configured in compiz...

Don't know anything about that,sry.

---

### Post by mcduck on 2010-03-10
> **Obontoo said:**
> In compiz config (opacity, brightness and saturation) , I have window value set at 80 for "any" windows. This gives all windows opacity. However, I don't want the panels to have opacity.

I want all windows except the panel to have opacity. What code do I write under "Windows" which will affect all windows except the panels?

Thanks
/Obontoo

replace the "any" with "!(class=Gnome-panel)"

(Gnome-panel uses window class "Gnome-panel", and the "!" equals "not", so this rule will affect any window that *isn't* of class "Gnome-panel". You could also use"!(type=Dock)" but that would also affect other dock applications instead of just Gnome-panel, and in addition the popup menu from the clock applet uses the same type so it would become transparent as well.)

---

