---
title: "font has changed in firefox browser"
date: 2011-03-30
forum: Desktop Environments
---

### Post by Reyjisan on 2011-03-30
Hello!

Wondering if you guys can help me troubleshoot a problem. After installing Linux Multimedia Studio the fonts on my firefox4 browser has slightly changed. I remember during the installation that it installed some fonts so maybe it has something to do with that.

The default font settings on my firefox has remained the same but it looks different than before. On certain websites like facebook the main font looks different. I uninstalled LMMS thinking it would bring back the default font settings but it hasnt.

Any ideas how I can bring it back to my default settings on firefox? Thanks very much in advance.

---

### Post by Hashiru on 2011-03-30
If after installing fonts some pages are displayed differently now, they tried to use the missing font in the first place.

There are several ways of solving this:
1. Force firefox to use a certain font
2. Remove the unwanted font
3. Use a font manager

1.
Force your font to remain the same in firefox. Although I can imagine you don't want to do that, here is how its done:
In firefox Edit->preferences
choose the tab "content" and under the fonts and colors choose advanced
There is a checkbox there that allows pages to use their own font, uncheck that to force your own font.

2.
The second option is removing the font that is displayed now. You can figure out which font you want to remove by selecting some text in the font you want to remove and paste it in openoffice. Place the cursor anywhere in the text and it should display which font you are using.
To remove the font:
use rm filepath to remove a font. The fonts are probably somewhere in /usr/share/fonts/truetype. After that "sudo fc-cache -fv" from the terminal should fix it.

3.
I just installed fontmatrix from the ubuntu software manager and in this application you can enable or disable fonts. A reboot might be needed to apply the changes.

If I were you I would go for solution three.

Hope this helps.

---

### Post by Reyjisan on 2011-03-31
Thanks for your response. I downloaded fontmatrix. I couldn't seem to change the font its a minor issue but I think I can live with it.

---

