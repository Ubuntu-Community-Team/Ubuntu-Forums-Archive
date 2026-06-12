---
title: "How do I return to default theme font sizes?"
date: 2007-02-27
forum: Desktop Environments
---

### Post by SumChipper on 2007-02-27
I was messing around with the themes and applied Large Print. Now when I apply Human everything changes except for the font size (it is still large). How do I get back to the default font sizes in Human?

Thanks!

---

### Post by SumChipper on 2007-02-28
No ideas? I'm not finding anything online for this.

---

### Post by ComplexNumber on 2007-02-28
> **SumChipper said:**
> I was messing around with the themes and applied Large Print. Now when I apply Human everything changes except for the font size (it is still large). How do I get back to the default font sizes in Human?

Thanks!
go to your main menu -> system -> preferences -> fonts.

actually, you may just to log out and then log back in again to refresh the xserver. try that first.

here is the screenshot of default font sizes:

---

### Post by SumChipper on 2007-02-28
Thanks! I guess the default is 10 all the way down. Easy to remember.

I also came across a way to "reset" gnome by typing the following in the shell:

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Anyway, thanks again for the screenshot. Other than this little thing, ubuntu has been super so far. All hardware recognized and I was online doing updates and stuff without even glancing at the system panel. :)

---

### Post by ComplexNumber on 2007-02-28
> **SumChipper said:**
> Thanks! I guess the default is 10 all the way down. Easy to remember.

[B] I also came across a way to "reset" gnome by typing the following in the shell:
[/B] 
** rm -rf .gnome .gnome2 .gconf .gconfd .metacity**

Anyway, thanks again for the screenshot. Other than this little thing, ubuntu has been super so far. All hardware recognized and I was online doing updates and stuff without even glancing at the system panel. :)
you really don't want to that all the time (especially when you are logged in to gnome. if you have to do that, log out and choose the failsafe terminal, then do it).  most of your settings and stuff are in .gnome2 and .gconf. erasing them will reset everything to what it was when you first logged in to gnome. if at any time you run into a problem that you feel that you can't solve any other way other than deleting those files, consider renaming them instead of deleting them (eg renaming gconf to gconf-OLD or something).

glad you sorted it anyway :)

---

### Post by fsando on 2007-03-11
> **ComplexNumber said:**
> go to your main menu -> system -> preferences -> fonts.

actually, you may just to log out and then log back in again to refresh the xserver. try that first.

here is the screenshot of default font sizes:I'm having a problem here:
I changed the screen resolution, changed it back to the original. After that when changing the application font has no effect. Changing other fonts work. This only happens in an XGL session not a normal gnome session.

UPDATE:
I found a solution: have the gnome-settings-daemon start automatically.
Add the command 'gnome-settings-daemon' in **System > Preferences > Sessions > Startup Programs**. It Works perfectly - Though I believe it should be started somewhere else in the startup process so it probably isn't the most elegant way.

Perhaps someone could shed some light on this?
Some further questions: 
Where do the panel, applications etc. read the font settings?
Where does the gnome-settings-daemon read its settings?

---

