---
title: "Changing appearance theme from command line or shortcut?"
date: 2011-06-08
forum: Desktop Environments
---

### Post by egarrulo on 2011-06-08
Hello,

is there a way to change appearance theme (the way you can do from: Menu -> Preferences -> Appearance -> Theme, that is, by running  "gnome-appearance-properties") from command line or keyboard shortcut?

I'd like to be able to switch easily between at least two color themes, one for day and one for night.

Thanks.

---

### Post by Copper Bezel on 2011-06-09
Yep. = ) For example,

```
gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme Ambiance
gconftool-2 --type string --set /apps/metacity/theme Ambiance
```

---

