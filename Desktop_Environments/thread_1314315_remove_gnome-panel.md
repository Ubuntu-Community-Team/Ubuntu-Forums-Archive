---
title: "remove gnome-panel"
date: 2009-11-04
forum: Desktop Environments
---

### Post by mihaicj on 2009-11-04
Does anybody know a way to make gnome-panel not visible in Karmic? I'm using a dock so I don't really need the panel. Thanks.

---

### Post by kensum on 2009-11-04
right click and choose properties. Autohide and show hidebuttons

---

### Post by 73ckn797 on 2009-11-04
For the bottom panel right click on the panel and delete panel. Good idea to have the top panel available via auto hide as mentioned already.

---

### Post by mcduck on 2009-11-04
The only way to get rid of the panel, if you don't need it, is to remove it from your Gnome session through gconf-editor. Of course you can configure some other app to run in it's place if you want to. :)

Removing the last panel isn't possible, and as long as the panel is running as Gnome component it will automatically spawn back if you try to kill it.

So, if you want to remove the Gnome-panel from your desktop you need to start gconf-editor and then remove "panel" from the list in desktop/gnome/session/required_components list (and perhaps also unset the desktop/gnome/session/required_components/panel -key).

But if you are planning to just run some other panel or dock instead it would make sense the leave the panel in the session components, and then just set the desktop/gnome/session/required_components/panel to use whatever program you are planning to run. This would automatically start that app for you and also autospawn it back if it crashes or is killed.

Also note that if you disable Gnome-panel you will loose the Alt-F2 Run dialog as well, so make sure you have some other way to start applications that the Run dialog and panel menus.. If you want similar functionality without running the Gnome-panel Gmrun is a nice app for the purpose, just set Alt-F2 as keyboard shortcut to launch it.

---

### Post by JugglinPhil on 2009-11-04
If those suggestions answered your question you might want to mark this as solved.

---

### Post by mihaicj on 2009-11-04
In Jaunty there used to be a way to put the panel on another screen, even if it didn't actually exist. For example you have one screen (screen 0) but you put the panel on screen 1. Now that doesn't work anymore. Maybe there is another workaround like this one.

---

### Post by mihaicj on 2009-11-05
Does anybody know a better workaround?

---

### Post by hossdozero on 2009-11-06
I'm also curious about how to do this.
The gnome panel is just unnecessary clutter while using cairo

EDIT:

Nevermind, Tried the second option listed by mcduck. seems to work fine...for now.

---

### Post by ravosava on 2010-02-18
> **mcduck said:**
> The only way to get rid of the panel, if you don't need it, is to remove it from your Gnome session through gconf-editor. Of course you can configure some other app to run in it's place if you want to. :)

Removing the last panel isn't possible, and as long as the panel is running as Gnome component it will automatically spawn back if you try to kill it.
[B]
So, if you want to remove the Gnome-panel from your desktop you need to start gconf-editor and then remove "panel" from the list in desktop/gnome/session/required_components list (and perhaps also unset the desktop/gnome/session/required_components/panel -key).

But if you are planning to just run some other panel or dock instead it would make sense the leave the panel in the session components, and then just set the desktop/gnome/session/required_components/panel to use whatever program you are planning to run. This would automatically start that app for you and also autospawn it back if it crashes or is killed.[/B]

Also note that if you disable Gnome-panel you will loose the Alt-F2 Run dialog as well, so make sure you have some other way to start applications that the Run dialog and panel menus.. If you want similar functionality without running the Gnome-panel Gmrun is a nice app for the purpose, just set Alt-F2 as keyboard shortcut to launch it.

how do you do this?

---

### Post by samigina on 2010-02-18
This way (see the attachment)

Change the value of Panel to blank or to the command for your dock.

---

### Post by gameplace123 on 2010-08-07
Thanks mcduck. if using ALT+F2 is important to anyone, you can replace it with [gRun]("http://code.google.com/p/grun/") (search for it in Synaptic). It's pretty much like the run dialog in Windows. After installation, just bind it to the ALT+F2 keys... DONE.

---

### Post by propan0 on 2010-10-01
> **samigina said:**
> This way (see the attachment)

Change the value of Panel to blank or to the command for your dock.

Awesome, exactly what I needed to do, an image speak a thousand words - thanks!

Note that by doing this you stil keep the alt-f2 for launching programs. I only use it for when gnome-do crashes on me, but hey, it's not that uncommon hehe =)

---

### Post by papabean on 2010-10-16
Pity this forum doesn't allow marking particular posts as friendly, helpful, solution, etc.  mcduck provided a perfect solution with alternatives.

Thanks for the assist, mcduck.  It helped me, too.

---

### Post by ck1991 on 2011-09-04
any solution for 11.04?

---

### Post by Krytarik on 2011-09-04
> **ck1991 said:**
> any solution for 11.04?
Please see this guide:

[http://www.tuxgarage.com/2011/05/run-awn-dock-in-natty-narwhal.html](http://www.tuxgarage.com/2011/05/run-awn-dock-in-natty-narwhal.html)

Greetings.

---

