---
title: "Is it possible to theme/edit tooltips?"
date: 2009-05-11
forum: Desktop Environments
---

### Post by Fzang on 2009-05-11
You know, when you mouse over something an ugly yellow/grey tooltip will appear and it looks so outdated. Is it possible to theme/edit the colors of these tooltips in GNOME?

---

### Post by mcduck on 2009-05-11
> **Fzang said:**
> You know, when you mouse over something an ugly yellow/grey tooltip will appear and it looks so outdated. Is it possible to theme/edit the colors of these tooltips in GNOME?

Yes, the colors can be changed, and if you use Compiz (the "desktop effects"), you can also make tooltips transparent.

First, check if the GTK theme you are currently using allows for customizing colors. Go to System/Preferences/Appearance-tab and click Customize-button. If you are lucky you will be able to change the tooltip colors on the colors-tab.

If that option was greyed out, you'll have to do it in a bit more tricky way. Create a file caled ".gtkrc-2.0" in your home directory and open that with a text editor. Then paste the following piece of code into that file:
```

style "tooltip"
{
  bg[NORMAL] = "#ffffff"
  fg[NORMAL] = "#000000"
}

widget "gtk-tooltips" style "tooltip"
```
Of course you can change the color codes to what you want . The first one is background, second one text. When done, save the file and log out & back again and your tooltips should now use these custom colors.


For transparency, open CompizConfig Settings Manager, go to "Opacity, Brightness and Saturation"-plugin and on the "Opacity"-tab add new rule. Set the "Windows"-string to "type=Tooltip" and adjust the transparency as you wish. (Note that this will make the whole tooltip transparent, including text, so don't use too low values or you won't be able to read the tooltups any more. I suggest something around 80-95...

---

### Post by ibuclaw on 2009-05-11
You can also opacify other elements too that add a nice touch:
```
Tooltip | Menu | PopupMenu | DropdownMenu
```
Setting the Windows Values to 95 should be just fine.

Regards
Iain

---

### Post by Fzang on 2009-05-11
Awesome, thanks :)

...I don't suppose you know how to make semi transparent right click menus? :D

EDIT: Dam, that was faster than I had expected :p

---

### Post by ibuclaw on 2009-05-11
> **Fzang said:**
> EDIT: Dam, that was faster than I had expected :p

I must have had one of those pre-emptive answer moments, where I knew the question before it was asked ... ;)

---

