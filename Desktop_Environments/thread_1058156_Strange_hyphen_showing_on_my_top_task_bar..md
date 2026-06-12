---
title: "Strange hyphen showing on my top task bar."
date: 2009-02-02
forum: Desktop Environments
---

### Post by Tom_T on 2009-02-02
Not a major issue, but it's just sat there..

How do I remove this lone some hyphen from my top task bar.??

Please see the attached taskbar.gif
It's the little white hyphen ' - ' !!

Thanks

---

### Post by mbeierl on 2009-02-02
When you mouse-hover over it do you get any pop-up?  Try right clicking on it to see if it's a widget of some sort?

What happens to it when you move your system notification area around it?

---

### Post by Tom_T on 2009-02-02
Nothing happens when I move my mouse over it. Right clicking just shows the normal panel menu and moving other items it jsut moves with them..

Nothing else appears.

---

### Post by mbeierl on 2009-02-02
So it always stays to the left of the system notification as shown in your screen shot?  Or does it pop to the right of it when you move sys notif to the left?

I have this vague feeling that it looks like the "remaining charge time" of a battery that's fully charged.  Do you have a battery and can you switch to battery power and see if it responds?

---

### Post by Tom_T on 2009-02-02
Swapping from mains to battery hasn't made any difference. I've managed to move the battery charge and the wireless icons, but the hyphen has stayed in the same place.

Bizarrely I can't move the battery / wireless icons back they go so far to the left but then stop. It's like the hyphen is blocking them !!

Any way to just reset the top taskbar ?? Thanks

---

### Post by Tom_T on 2009-02-02
hmm. something strange my battery and wireless icons have just gone !!

Is there any quick way to reset the taskbar ??

---

### Post by Tom_T on 2009-02-02
a reboot has removed the hyphen...  It looks like it was left over from when I had Glipper installed..

Now how do I get the original power/battery monitor and wireless icons etc back ?

---

### Post by Tom_T on 2009-02-02
Sorted .. :) 

Just added notification area back to the panel and they reappeared .

---

### Post by mbeierl on 2009-02-02
Sorry - went away for a little bit there.

As an aside if you want to fine tune your Gnome panel, you can use gconf-editor and go under:

apps -> panel -> toplevels

and under there you'll find object names like "top_panel_screen1" which has info on placement, colour, autohide, etc.  Unfortunately the applets loaded on the panel are not listed there.

Does anyone know where to find that in gconf-editor?

---

