---
title: "How to fix broken Font Preferences?"
date: 2005-05-09
forum: Desktop Environments
---

### Post by emendelson on 2005-05-09
Can anyone tell me where the Gnome "Font Preferences" dialog stores its preferences? When I use System/Preferences/Font, the choice for "Windows Title Font" is grayed out (permanently set to Bitstream Vera Sans 10). All the options on this menu work normally, but Windows Title Font is grayed out and can't be changed. I would like to try trashing  the preference file (wherever it is) and starting over, if possible. But I can't find the file.

There seems to be nothing wrong with the Bitstream Vera Sans font - I can choose it for other uses (such as Desktop Font). The same problem occurs if I login as a different account (including root).

The problem started when I tried to use this hint to add Frutiger to the menu

[http://ubuntuforums.org/showthread.php?t=30357](http://ubuntuforums.org/showthread.php?t=30357)

I added the Frutiger fonts to /usr/X11R6/lib/X11/fonts/Type1, ran fc-cache -fv to refresh the font cache, and tried to select a Frutiger font in the Windows Title Font menu item. After closing the menu, the earlier choice of Bitstream Vera Sans 10 was still chosen. I've deleted all the Frutiger fonts, rebooted, run fc-cache again, but I can't get that grayed-out menu item to become active again.

Any help gratefully received.

---

### Post by Alexander Kirillov on 2005-05-09
[QUOTE=emendelson]Can anyone tell me where the Gnome "Font Preferences" dialog stores its preferences? When I use System/Preferences/Font, the choice for "Windows Title Font" is grayed out (permanently set to Bitstream Vera Sans 10). All the options on this menu work normally, but Windows Title Font is grayed out and can't be changed. I would like to try trashing  the preference file (wherever it is) and starting over, if possible. But I can't find the file.

There seems to be nothing wrong with the Bitstream Vera Sans font - I can choose it for other uses (such as Desktop Font). The same problem occurs if I login as a different account (including root).

The problem started when I tried to use this hint to add Frutiger to the menu

[http://ubuntuforums.org/showthread.php?t=30357](http://ubuntuforums.org/showthread.php?t=30357)

I added the Frutiger fonts to /usr/X11R6/lib/X11/fonts/Type1, ran fc-cache -fv to refresh the font cache, and tried to select a Frutiger font in the Windows Title Font menu item. After closing the menu, the earlier choice of Bitstream Vera Sans 10 was still chosen. I've deleted all the Frutiger fonts, rebooted, run fc-cache again, but I can't get that grayed-out menu item to become active again.

Any help gratefully received.[/QUOTE]


It is stored in gconf peferences (directory ~/.gconf) - but there are very many settings in this directory. You can try editing it directly using gconf-editor (look for apps-metacity-general)

---

### Post by emendelson on 2005-05-09
Alexander,

That pointed me in the right direction - thank you. The solution to the problem is this:

If "Window Title Font" is grayed out in System/Preferences/Font, then use Application/System Tools/Configuration Editor (which is gconf-editor), and then under apps/metacity/general, REMOVE the checkbox from "titlebar_uses_system_font".

This must be one of the worst examples of user-interface design in modern times. Surely the Gnome developers can include a way to "take back" the Window Title Font inside the main Font Preferences dialog.

Thanks again,

Edward Mendelson

---

