---
title: "place windows from each app next to one another"
date: 2010-07-30
forum: Desktop Environments
---

### Post by gobbles414 on 2010-07-30
Recent versions of Microsoft Windows automatically place windows from each app next to one another -- Internet Explorer windows next to other Internet Explorer windows, Excel windows next to other Excel windows, etc.

Is this possible in a Ubuntu panel? The closest I can find is the "always group windows" option in the window list properties. I don't want to "group" the windows unless I run out of room in the panel; I want windows from each app to be next to one another -- Firefox next to Firefox, OpenOffice next to OpenOffice, etc.

I'm running GNOME 2.28.1 in Ubuntu 9.10. Thanks in advance for your help!

---

### Post by JonasDK on 2010-07-30
Do you mean the buttons in your **panel** or the windows **itself**? Because if you mean the windows itself, then you can achieve that fairly easy with Compiz. If you go to the advanced Compiz settings you can set up your own shortcuts to let Ubuntu fill your desktop with two windows evenly across the screen. Just as you can in Windows.

```
sudo apt-get install compiz config-settings-manager  
```When you start that up go to 'Window Management'. This is actually a way to do it manually, to make Ubuntu fill your workspace evenly with multiple programs. Don't know if you can make Ubuntu recognize programs and fit them accordingly.

Greets,
Jonas

---

### Post by gobbles414 on 2010-07-30
Thanks for your reply JonasDK.

I'm referring to the buttons in the panel. Ubuntu places "window list" buttons in the panel based upon when they were first opened, with an option to manually drag each button into a different position.

What I want instead is for Ubuntu to automatically organize the buttons based upon the program to which each belongs -- all Firefox windows next to each other, all Evolution windows next to each other, etc.

---

### Post by Marctwo on 2010-07-30
I couldn't get the gnome-panel task bar to do it but I now use AWN in place of my bottom panel.  AWN does follow this behaviour if you choose not to group icons - but AWN may not suit your other needs.  May be worth a try though.

---

### Post by skooter1121 on 2010-07-30
I use the attached windowing program.

Please note that I have only installed it on systems with compiz disabled, so I do not know if that will effect it.

It works great on my Asus 900a netbook. Just click on the panel icon and unmaximized windows tile.

You could also look at a new program called x-tile that does something similar.


-SK

---

### Post by gobbles414 on 2010-08-01
I tried AWN, but the dock style isn't a good match for my needs. Furthermore, a couple of the AWN applets that I'd need are somewhat buggy.

I also tried x tile; unless I'm missing something, it doesn't do what I need. I didn't try the attached tile program, since skooter1121 reports that it's similar to x tile.

Allow me to clarify what I'm seeking: I'm not trying to manipulate the windows themselves. Instead, I'm attempting to get Ubuntu to automatically sort by app the panel/taskbar BUTTONS which represent the windows -- as is standard taskbar behavior in newer versions of Microsoft Windows. Let's say that I'm editing several OpenOffice documents while surfing the web via a couple of Firefox windows... I want all of the buttons which represent the OpenOffice windows to be next to one another in the panel, and then the buttons representing my Firefox windows next to one another in the panel as well.

Thanks again for the ideas... Please, keep them coming! :-)

---

### Post by gobbles414 on 2010-08-10
bump

---

