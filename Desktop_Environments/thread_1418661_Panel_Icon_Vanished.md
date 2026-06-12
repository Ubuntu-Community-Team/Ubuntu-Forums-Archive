---
title: "Panel Icon Vanished"
date: 2010-02-28
forum: Desktop Environments
---

### Post by lordjubblydave on 2010-02-28
I hope im in the right forum.
Im running Ubuntu 9.10 and for some reason my Wireless icon changes itself to a sound  randomly.
[IMG]http://i306.photobucket.com/albums/nn253/lordjubblydave/Screenshot.png[/IMG]

I can get it back to how it should look by removing and adding the notification applet to the panel, although every time i reboot it reverts back to how it looks in the picture.
Any ideas as to why ? and how to stop this happening ?

---

### Post by soldar79 on 2010-02-28
It's no big deal. There's an applet (the little apps you run on the gnome panel), which you can access by right-clicking on the panel and choosing +ADD TO PANEL, which is related to tray icons: notification area. You just need to quit it by rightclicking on the tiny strips icon next to the volume manager, and then re-add it the way i've explained: choosing +ADD TO PANEL -> notification area.

Just that, hope it works.

J.

---

### Post by lordjubblydave on 2010-02-28
Thanks for your help, but that is what i have been doing.
But the thing is it should not happen, so i want to stop it from happening

---

### Post by ubeautu on 2010-03-03
I installed Amorak (KDE) today to Ubuntu 9.10 and i lost both my volume control and wifi control from the top right panel. I assume it was something to do with the KDE app being installed in Gnome? Anyway, I cant see them anywhere in the 'add to panel' list. Any ideas?

---

### Post by delectate on 2010-03-03
remove tray and re-add tray to gnome-panel

or```
 killall gnome-panel
``` to restart gnome-panel

usually,i do last one,it works...

---

### Post by ubeautu on 2010-03-03
Thanks Delectate,
Managed to fix it just now. The lost Wifi, bluetooth and Volume control are in 'notification area'. Just had to right click on the panel and add it 'notification area'. 

 :popcorn:

---

