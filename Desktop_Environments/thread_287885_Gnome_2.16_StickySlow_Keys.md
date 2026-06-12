---
title: "Gnome 2.16 Sticky/Slow Keys"
date: 2006-10-29
forum: Desktop Environments
---

### Post by hahafaha on 2006-10-29
Hi all,

I recently upgraded to Edgy Eft which comes with Gnome 2.16. A feature in it is Sticky/Slow Keys. Although they are disabled by default, clicking shift five times in a row or holding down shift for more than 8 seconds, pops up an annoying dialog box asking whether or not I want to enable them. I do not need them, but occasionally do need to click shift 5 times or hold it down for 8 seconds (for example, with the GIMP). Is there a way to disable sticky keys entirely (i.e. never asking me about it?)

Thanks in advance!

--
Leonid Grinberg
[email]lgrinberg@gmail.com[/email]

---

### Post by xyz on 2006-12-21
Found this for K! Any Gnome equivalent anyone?
Go to K > System Settings > Regional & Accessibility (near the top) > Accessibility > Keyboard Filters > Uncheck "Use slow keys"

---

### Post by sedd on 2006-12-26
My favorite part about the "Do you want to activate slow keys?" dialog is that it pops up _under_ all the open windows, and grabs keyboard focus _from X_ so that no keys work, not even ctrl-alt-backspace, but the mouse still works, so you're sitting there thinking "oh crap I just broke the keyboard on this $X000 laptop and its not under warranty anymore!"  At least that's what happens to me.

Open gconf-editor and go to /desktop/gnome/accessibility/keyboard.
All the options are there. Uncheck the "enable" entry to turn off all accessibility options (better safe than sorry, right?)  The gnome docs make it sound like these options are all in the preferences menu for vanilla gnome, but ubuntu seems to have removed them. Pesky options...

Gnome: Simple usability for everyone! (who can use gconf-editor)

---

### Post by superm1 on 2006-12-31
> **sedd said:**
> My favorite part about the "Do you want to activate slow keys?" dialog is that it pops up _under_ all the open windows, and grabs keyboard focus _from X_ so that no keys work, not even ctrl-alt-backspace, but the mouse still works, so you're sitting there thinking "oh crap I just broke the keyboard on this $X000 laptop and its not under warranty anymore!"  At least that's what happens to me.

Open gconf-editor and go to /desktop/gnome/accessibility/keyboard.
All the options are there. Uncheck the "enable" entry to turn off all accessibility options (better safe than sorry, right?)  The gnome docs make it sound like these options are all in the preferences menu for vanilla gnome, but ubuntu seems to have removed them. Pesky options...

Gnome: Simple usability for everyone! (who can use gconf-editor)

Thank you so much!  This has been annoying more then anything about gnome for months.

---

