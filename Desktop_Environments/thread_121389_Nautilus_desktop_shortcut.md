---
title: "Nautilus desktop shortcut"
date: 2006-01-25
forum: Desktop Environments
---

### Post by seakiwi on 2006-01-25
Hi

I'm posting this in here even though I'm using Kubuntu, as my question is GNOME related. 

I've installed Nautilus (Konqueror is one of the few things I don't like about Kubuntu) but it hasn't shown up in the KDE menu anywhere (yes I did reboot to see if that helped). When I open it from the "run" command it opens fine, with the side pane enabled plus all the toolbars - which is the way I want it.

However, when I made a desktop shortcut (right click desktop add link to application) and pointed it at the Nautilus executable, it opens **without** that side pane, and with **no** options under "view" to add it, or any other toolbars. There is no way for me to get the setup I want with the side pane enabled, from that view that opens from the shortcut.

How on earth can I get the shortcut to open the program exactly as it opens from the "run" command? I've been sitting here racking my brains, trying everything I can think of and it's making me crazy!  ](*,) 

Either I'm missing something very obvious, or this is very weird behaviour. If anyone has any idea how to do this I'd be very grateful. 

TIA!

---

### Post by Bou on 2006-01-25
I think you should try pointing the shortcut to "nautilus --browser". :)

What you're using now is the spatial mode of Nautilus, where every folder is treated as a physical object ad its size and position is remembered. Much better in my opinion, I would give it a try.

---

### Post by Sutekh on 2006-01-25
This is my entry in Applications
```
nautilus --no-desktop --browser %U
```
I'm not sure what the no-desktop means though

---

### Post by seakiwi on 2006-01-25
[QUOTE=Bou]I think you should try pointing the shortcut to "nautilus --browser". :)

What you're using now is the spatial mode of Nautilus, where every folder is treated as a physical object ad its size and position is remembered. Much better in my opinion, I would give it a try.[/QUOTE]

Thankyou! :mrgreen: 

That was driving me nuts! **NOW** I can go to bed! :KS

---

### Post by Bou on 2006-01-25
G'night mate, though it's almost noon here!

---

