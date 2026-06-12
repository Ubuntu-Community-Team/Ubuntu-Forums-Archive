---
title: "Desktop icons aren't initially appearing on the desktop"
date: 2008-12-14
forum: General Help
---

### Post by fwaokda on 2008-12-14
I am using Ubuntu 8.10 and I have been downloading things to my desktop and yet when I have there are no new icons on the desktop (just my recycle bin).  Only after I click on "Places>Desktop" can I see the files there, and after I see the files there they then show up on the desktop like they should have all along.  How can I fix this? TY

---

### Post by pastalavista on 2008-12-14
In the command prompt (alt-f2) type 'gconf-editor'. Then in the tree open-- apps/nautilus/preferences and make sure 'show desktop' is checked.

---

### Post by northern lights on 2008-12-14
> **pastalavista said:**
> apps/nautilus/preferences and make sure 'show desktop' is checked
If 'show desktop' was disabled, nautilus would not draw one at all. So going the "Places > Desktop" route would not result in anything either.

---

### Post by pastalavista on 2008-12-14
@northern lights -- I just tested it. I unchecked the box and the desktop icons disappeared but they were still in the places/desktop menu view and when I clicked on one, they all re-appeared on the desktop. where did you get your information?

---

### Post by fwaokda on 2008-12-14
> **pastalavista said:**
> In the command prompt (alt-f2) type 'gconf-editor'. Then in the tree open-- apps/nautilus/preferences and make sure 'show desktop' is checked.

I've looked to see if it was checked and it was.  So I'm still having the problem.  Thanks for you replies!

I have recently installed this...
sudo apt-get install gtweakui

As I was trying to get a recycle bin icon on the desktop and this was the recommended way of doing so in the ubuntu irc channel.

---

### Post by northern lights on 2008-12-15
> **pastalavista said:**
> @northern lights -- I just tested it. I unchecked the box and the desktop icons disappeared but they were still in the places/desktop menu view and when I clicked on one, they all re-appeared on the desktop. where did you get your information?

They certainly will remain in the respective folder (/home/USER/Desktop/). However, if 'show desktop' is diabled, opening /home/USER/Desktop either via the home folder or from the Places menu will not result in them thereupon being drawn on the actual desktop if the option remains disabled. Which is what happened/happens to the OP.

Where did the info come from?
I work without a desktop, since icons annoy the crap outta me. However the folder is once in a while accessed...

> **fwaokda said:**
>  [...] and after I see the files there they then show up on the desktop like they should have all along [...] 




> **fwaokda said:**
> I have recently installed this...
sudo apt-get install gtweakui
What options did you alter?

Anyhow, this GUI also simply uses *gconf-editor* as a backend. Still, it's beyond the shadow of a doubt not the 'show desktop' option that we are concerned with. Though it is an option in *gtweakui-nautilus*.
You could have enabled the trash via *gconf-editor* and /apps/nautilus/desktop/trash_icon_visible - That's the swith that *gtweakui* accesses anyhow.

As far as your problem is concerned, nothing in *gtweakui-nautilus* should have caused it.
Did it repeatedly happen and remain a the case today?

---

### Post by havencruise on 2008-12-15
have you changed any of the mount points in your fstab manually?

---

