---
title: "terminal keyboard shortcut not working"
date: 2007-03-20
forum: Desktop Effects &amp; Customization
---

### Post by fartonmyear on 2007-03-20
i can't seem to make my terminal keyboard shortcut work. i think it's because of beryl. anyone else have this problem?

---

### Post by joyolee on 2007-03-21
if you set your shortcuts via configuration-editor

you have to reset it 

beryl setting management-----------general option-----------command/shortcuts

---

### Post by fartonmyear on 2007-03-21
i don't know what you mean by that.

---

### Post by jterroux on 2007-04-07
I am having the same problem.  Can you explain with a little more detail on how to fix this?  Thanks

---

### Post by e_man_88 on 2007-04-08
I have the exact same problem as well. The shortcut worked fine, but after installing Beryl, it stopped working. I checked the Beryl's shortcuts to see if there were any conflicts, but there doesn't seem to be any. Does anyone know how to fix this?

---

### Post by jterroux on 2007-04-08
I managed to get it working with compiz.  I had to go into the compiz settings and turn on the keybinding plugin.  Then i went to the configuration editor and when to apps>compriz>options>allscreens and scrolled down to find they entries for key shortcuts and make sure they were set up to the way i wanted.  Everything seems to be working except for beagle's shortcut.  But i think i had a bad install of it and it never worked before so..  Good luck with beryl.  Hope this can help.

---

### Post by e_man_88 on 2007-04-08
I couldn't find a binding option for the terminal in Beryl's shortcuts. Maybe I've overlooked it? Or perhaps Beryl is different from Compiz?

The only thing I've managed so far is to set Beryl's command 0 as "xterm", and bind a key combination for it. But this really isn't addressing the problem, as I believe xterm is simply an emulator for the terminal.

Is there a way so I can bind the actual terminal?

---

### Post by Error47 on 2007-04-11
I am also having the same problem, trying to get it fixed too. Another shortcut that no longer works is the switching between viewports, I used to have a shortcut like ctrl + > goes to the next desktop, but that no longer works. Anything to fix that?

---

### Post by Jaygo333 on 2007-04-11
Same here. Had the same problem when I had beryl. 
The only way I seemed to fix it was to put the shortcuts onto the tasbar.

Most of my shortcuts led to beryll stuff. I loved binding things with the Super_L key. In beryl, that key is used to start and stop visual stuff.(rain on desktop e.t.c)

---

### Post by jterroux on 2007-04-11
Maybe just go into the config editor and check the beryl entry and see if there are any options for key bindings or shortcuts and make sure they are configured the way you want them.  Thats all I had to do to fix my problem I was having with compiz.   Good luck.

---

### Post by novaraz on 2007-04-12
Ubuntu's default keyboard-shortcuts are managed by Metacity.  When you use Beryl as your windows manager, you lose your mapped Metacity shortcuts.

One simple way to enable the terminal shortcut in Beryl is to map your keyboard shortcut in "Beryl Settings Manager" -> Shortcuts -> General Options -> Run command0.  Mine is set as <Ctrl><Alt>x.  Then go to General Options (the icon, not tab), the tab "Commands" and set command0 as "gnome-terminal".

You can also use xbindkeys to set shortcuts regardless of the windows manager.  Just apt-get xbindkeys and xbindkeys-config.

---

### Post by Error47 on 2007-04-12
wow, good tip! That worked very good. Thanks!

---

### Post by Gadren on 2007-04-21
Thank you so much, novaraz!  This worked like a charm... so many other guides had part of the solution, but yours followed it through to the end.  I'd recommend you stick that guide into the Tutorials and Tips section.

---

### Post by e_man_88 on 2007-05-28
> **novaraz said:**
> Ubuntu's default keyboard-shortcuts are managed by Metacity.  When you use Beryl as your windows manager, you lose your mapped Metacity shortcuts.

One simple way to enable the terminal shortcut in Beryl is to map your keyboard shortcut in "Beryl Settings Manager" -> Shortcuts -> General Options -> Run command0.  Mine is set as <Ctrl><Alt>x.  Then go to General Options (the icon, not tab), the tab "Commands" and set command0 as "gnome-terminal".

You can also use xbindkeys to set shortcuts regardless of the windows manager.  Just apt-get xbindkeys and xbindkeys-config.

Thank you very much! This is the solution I've been looking for. Now my keyboard shortcut to the terminal works perfectly while running beryl.:D

---

### Post by brandon079 on 2007-09-28
I honestly thought I was having this same problem with compiz. I kept restarting, unchecking apps from session manager, changing key binding in compiz etc etc. Then I realized my f-lock key wasn't on. I'm gonna bang my head on the desk now for good measure.

---

