---
title: "Changing Gnome clock?"
date: 2007-01-11
forum: Desktop Environments
---

### Post by rabid emu on 2007-01-11
I like to have transparency for my taskbar, and sometimes when I have a dark wallpaper I can't really see the clock.  I've been searching but I can't find a way to change the color or font of the clock on the gnome taskbar.  I've been searching for an alternative, and the only one I've seen is fdclock but I can't find any options for that (it has no man pages apparently...)  I'm running Xgl and Beryl if that matters.

Anyone have a solution for me?

---

### Post by mcduck on 2007-01-11
Create a file called '.gtkrc-2.0' in your home directory, and paste the following code to the file:
```
style "panel-clock"
{
  fg[NORMAL] = "#000000"
}
widget "*.clock-applet-button.*" style "panel-clock"
```
Then change the color code to whatever you want, log out and back again. :)

---

### Post by rabid emu on 2007-01-11
Thanks a lot!  Additionally how can I bold the text to make it even more visible?  Or perhaps add an outline to it?

---

### Post by paparucino on 2007-01-11
> **mcduck said:**
> 
Then change the color code to whatever you want, log out and back again. :)
Great job.
I should like to have another feature, if you can.
I love transparencies too so I'ld like to have the background of the active window without the grey background. is it possible?
and... ahem... if you can help... how can I remove the text next to the icon?

Thank you in advance.

---

### Post by mcduck on 2007-01-11
I suppose it would be possible to change the font for the clock applet somehow, but I have no idea what to add to that code to do this.

And transparency is not really well supported in GTK, the only way I know (apart from some apps that have it built in) is to use Compiz or Beryl and let it make your windows transparent. But that affects all of the window, including text, and not only the background.

---

### Post by mcduck on 2007-01-11
> **paparucino said:**
> 
and... ahem... if you can help... how can I remove the text next to the icon?

umm. What icon? If you mean the Applications/Places/System-thing, right-click it and select 'Remove from Panel', the right-click on the empty space and select 'Add to Panel, find the 'Main Menu'-applet and drag&drop it to your panel.

---

### Post by paparucino on 2007-01-11
> **mcduck said:**
> umm. What icon? If you mean the Applications/Places/System-thing, right-click it and select 'Remove from Panel', the right-click on the empty space and select 'Add to Panel, find the 'Main Menu'-applet and drag&drop it to your panel.
Suppose to have firefox running, on the panel you see the firefox icon and some other information about the site you are visiting. In this case "Ubuntu forums - Reply to Topic - Swiftox". I'ld like to remove the written part "Ubuntu ...."

---

### Post by mcduck on 2007-01-11
> **paparucino said:**
> Suppose to have firefox running, on the panel you see the firefox icon and some other information about the site you are visiting. In this case "Ubuntu forums - Reply to Topic - Swiftox". I'ld like to remove the written part "Ubuntu ...."

Ok, now I got it. Sadly that's not possible in Gnome. It's one of the features in XFCE that I really hope Gnome would have..

---

### Post by tweedledee on 2007-01-13
> **mcduck said:**
> Ok, now I got it. Sadly that's not possible in Gnome. It's one of the features in XFCE that I really hope Gnome would have..

But you can get it.  Just install xfce4-panel, and run that - you want the icon box feature (I think, there are several choices).  You can also install xfce4-applet-plugin if you want to eliminate your gnome panels entirely and use your gnome applets on the xfce4-panel.  Unfortunately, the xfce4-panel does not support transparency, so you're stuck with a gray (or whatever color) panel.

---

