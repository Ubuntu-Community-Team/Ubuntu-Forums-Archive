---
title: "Ubuntu 10.10 Keyboard layout switch automatic"
date: 2011-01-08
forum: Desktop Environments
---

### Post by Gorbusch on 2011-01-08
I have 
  ubuntu 10.10  (System is up to date with updates)
  kernel 2.6.35-24
  gnome 2.32.0
with two keyboard layouts US and German, US is on the top of the list.

System itself is installed as English. Although location is Austria.

Whenever i open a window not already opened in the session, like a chatwindow in skype, the keyboard layout is switching to german. I can change it back to US and it stays as long as i open no new window.

For Skype and chats it seems like having already opened a window to this contact is enough for the next opening of window to the same contact.


For me it looks a little bit like the settings are use different keyboard layout for each window and use default layout (how ever this got to be german).

So far i checked the keyboard layouts to have disabled all shortcuts changing the layout,
checked that the seperate layout option is disabled
and applied it system wide

Still going back to german for new windows.

---

### Post by Krytarik on 2011-01-08
Although I haven't researched it, it seems to be a bug in Gnome's handling of it's own keyboard layout preferences.

Does it work correct, if you have only one layout set up in the preferences?

Look here for a possible workaround, if you can't fix it in another way:
[http://ubuntuforums.org/showthread.php?p=10333055#post10333055](http://ubuntuforums.org/showthread.php?p=10333055#post10333055)

---

### Post by Gorbusch on 2011-01-09
When i just have one layout, it stays with this layout.

yesterday i enabled the option "seperate layout for each window" and "new window use active layout" and afterwards disabled both options again and then "applied system wide"

Till now no problem anymore with the layouts. Will reboot today to check if the problem reoccurs.

---

### Post by Krytarik on 2011-01-09
> **Gorbusch said:**
> When i just have one layout, it stays with this layout.

yesterday i enabled the option "seperate layout for each window" and "new window use active layout" and afterwards disabled both options again and then "applied system wide"

Just for my information, you did this as a possible fix, when the behaviour was already like described, right? And sorry, I didn't check the possible options before.
> **Gorbusch said:**
> 
Till now no problem anymore with the layouts. Will reboot today to check if the problem reoccurs.
I would be surprised if it changes after reboot/relogin.

---

