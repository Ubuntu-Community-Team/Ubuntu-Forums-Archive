---
title: "[SOLVED] Darklooks theme problems"
date: 2008-01-07
forum: Desktop Environments
---

### Post by absolutezero1287 on 2008-01-07
I'm using the Darklooks theme and I have a problem seeing tooltips. (I think that they're tooltips). They're those popups that come about when you have a new update or if you remove a device without unmounting it.

By default these tips are in yellow with black text. The problem is that Darklooks makes text white since all the background colors are dark. This is a minor annoyance but it makes my desktop imperfect and I don' want to remove darklooks. Can anyone help?

---

### Post by mcduck on 2008-01-07
If you want to change the tooltip colors for all themes, overriding the theme setting, you can do it like this:

1. Press Alt-F2 and run 'gedit ~/.gtkrc-2.0'

2. Paste this text to the file:
```

style "tooltip"
{
  bg[NORMAL] = "#FFFFFF"
  fg[NORMAL] = "#000000"
}

widget "gtk-tooltips" style "tooltip"

```

3. change the "#FFFFFF" and "#000000" to whatever colors you want. bg is the background color, and fg is for the text color.

4. save, logout and log in again. Now your tooltips will always use these colors, no matter what is defined in the theme you are using.

---

### Post by absolutezero1287 on 2008-01-08
Well, I tried that and the tooltips in Firefox and in other programs changed but not the ones on my desktop. They still remain yellow. However, the only ones that have white text are the alerts like when I have an update or if I remove a device without unmounting it first.

---

### Post by mcduck on 2008-01-09
> **absolutezero1287 said:**
> Well, I tried that and the tooltips in Firefox and in other programs changed but not the ones on my desktop. They still remain yellow. However, the only ones that have white text are the alerts like when I have an update or if I remove a device without unmounting it first.

OK, those are notifications, not tooltips ;)

You could try to set them to use the default style instead of the Ubuntu one. (IMHO the default style looks better anyway):

1. Press Alt-F2 and run 'gconf-editor'

2. Browse to apps/notification-daemon

3. Change the 'theme''-key's value to 'normal'

---

### Post by absolutezero1287 on 2008-01-09
Thank you for all that info, it really helped.

---

### Post by kakk on 2008-01-13
Hello,
I too like the darklooks theme, but still some problems, similar to discussed here, unsolved.

First, the openoffice. I do not use it much, but still. The notification or information bubbles that come to the screen when you move cursor over some button on the panel, are almost unreadable. Light background with light text. I managed to change the background from yellow to white with gconf-editor, as discussed here, but the text remains light gray. I have tried to change these colors from openoffice itself, but no luck. I managed to change some other openoffice colors from
Tools -> OpenOffice.org -> Apperance 
but not the "bubbles".

Second, I have a perl program using X that runs on another machine. this program lets me see some log files on its own graphical window, and when I open this window it is again gray text on white background. So where could I change a behaviour for such a program?

Regards,
Andres

---

