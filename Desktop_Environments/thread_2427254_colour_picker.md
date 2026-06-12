---
title: "colour picker"
date: 2019-09-19
forum: Desktop Environments
---

### Post by ajgreeny on 2019-09-19
There was a simple colour picker app called gcolor2 which is no longer available for 18.04, and gcolor3, the updated version for gtk3 is only available as a flatpack or from source.

However the xubuntu xfdesktop-settings can take you to a very similar utility as shown in my screenshot.
Is there is a command that will show just that utility without the main xfdesktop-settings window beneath?

---

### Post by Holger_Gehrke on 2019-09-20
I think that's just a dialog and not available as a standalone program. You could try [gpick]("http://www.gpick.org/") or zenity with the option '--color-selection'. Both are in the repositories.

Holger

---

### Post by ajgreeny on 2019-09-20
Thanks Holger.

I have seen **gpick** but was unaware of **zenity --color-selection**, but unfortunately neither allow me to pick a point on the screen with the cursor and show the hex colour code of that point; that is what gcolor2 did extremely quickly and easily.

Nevermind, I will just use the xfdesktop-settings utility as it's almost as simple; it just means one extra step but no big deal.

---

### Post by norobro on 2019-09-20
> **ajgreeny said:**
>  but unfortunately neither allow me to pick a point on the screen with the cursor and show the hex colour code of that point;gpick will do that. Try "gpick -p"

---

### Post by #&amp;thj^% on 2019-09-20
There is also a nifty tool called slickpicker

It's...a colorpicker written in PyQt?  that's all there is to this. (can also be used as a widget)

[https://github.com/ShadowKyogre/slickpicker](https://github.com/ShadowKyogre/slickpicker)

---

### Post by Holger_Gehrke on 2019-09-20
The tool you're looking for **is** available in gpick -- it's hiding in plain sight as a button in the lower right corner. It can also be activated with ctrl-p. If you then set "Spacebar button behaviour" to "Add to palette" in "Edit"->"Options" -> "Picker" you can hit 'ctrl-p' to activate the picker and then the spacebar on each color of interest and get a list of colors in the palette area of gpick's window. Right-clicking while the picker is active offers various notations for the color in a context menu and copies the selected notation for the color to the clipboard. If you set the program to minimize to the system tray, starting a drag on the icon in the tray gives you a picker, too ...

That's all just the tip of the iceberg, this thing has a lot of tools for people who need to work with colors.

Holger

---

### Post by ajgreeny on 2019-09-20
Gosh, I have learned a lot by asking that original question.

I missed the -p option in gpick completely (should have looked more carefully), but I think it is easier still to use the colour picker from the xfdesktop-settings and it requires no further package installations.

Thanks to all for the useful discussion.

---

