---
title: "Serious Compiz error, please help!"
date: 2009-01-31
forum: General Help
---

### Post by Shadow12313 on 2009-01-31
Something is really wrong with my computer, I just re-installed compiz desktop effects and now whenever I click on something inside a windows it moves it. I can't right-click on anything anymore and my screenlets are all messed up.

PLEASE HELP!

---

### Post by deepclutch on 2009-02-01
open a terminal and remove config file for compiz:
```
rm -r  ~/.config/compiz/ 
```

---

### Post by Shadow12313 on 2009-02-01
It didn't work.  I unistalled compiz and emerald, but still whenever I try to enable extra effects, the problem still shows up.

---

### Post by deepclutch on 2009-02-01
what is it says from terminal?
like.. open a terminal and invoke "compiz --replace"(without quotes).
and check for the trace in the terminal.
also ,make sure you have AIGLX enabled(and DRI too) on /etc/X11/xorg.conf
```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```
Try.oh! and what is your graphics card?by any chance ,is it a nvidia one?

---

### Post by Shadow12313 on 2009-02-01
> **deepclutch said:**
> what is it says from terminal?
like.. open a terminal and invoke "compiz --replace"(without quotes).
and check for the trace in the terminal.
also ,make sure you have AIGLX enabled(and DRI too) on /etc/X11/xorg.conf
```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```
Try.oh! and what is your graphics card?by any chance ,is it a nvidia one?

Yes I do have an nvidia card.  That only enabled the extra effects and started the problem again.
Any other ideas?

---

### Post by deepclutch on 2009-02-02
then ,
```
rm -rf ~/.compiz
```

---

### Post by geyids on 2009-02-02
I had problems with compiz conflicting and messing up the whole system until I realised that the settings are here so just remove compiz folder with

```
rm ~/.gconf/apps/compiz -r
```

hope that works out.

---

### Post by Shadow12313 on 2009-02-05
It still didn't work.  I tried re-installing it completely but it still won't work.  It seems to only happen when I enable extra or normal effects even with compiz and emerald removed.

Any ohter ideas?

---

### Post by Shadow12313 on 2009-02-14
I just reinstalled Ubuntu so the problem is gone now :)

---

