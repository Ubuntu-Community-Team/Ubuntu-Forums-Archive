---
title: "Nautilus Send to.../Send as"
date: 2005-03-31
forum: Desktop Environments
---

### Post by bonifacio on 2005-03-31
How do you add/change to the 'Send as'  drop down widget?  Right now it defaults to Evolution if I could add Thunderbird to the selection that will be great.

---

### Post by v79 on 2005-03-31
I'd also like to add "Send to Bluetooth" option. This sort of thing should really be scriptable, but I haven't found any documentation on it.

V79

[Edit] Looks like i'd have to write my own code and compile it as an so module. Which is beyond me.

---

### Post by Lord C on 2005-04-07
[QUOTE=v79]I'd also like to add "Send to Bluetooth" option.[/QUOTE]

Me too.

All I know is gnome-obex-send is the command :/

---

### Post by tanari on 2005-04-07
how can I remove this 'Send To' from menu? I don't use it.

---

### Post by kermy on 2005-04-07
Using the tip [here](http://ubuntuforums.org/showthread.php?t=24008) you could add a launcher to the toolbar that starts thunderbird or bluetooth with whichever file you dragged onto it.

---

### Post by Lord C on 2005-04-11
[QUOTE=kermy]Using the tip [here](http://ubuntuforums.org/showthread.php?t=24008) you could add a launcher to the toolbar that starts thunderbird or bluetooth with whichever file you dragged onto it.[/QUOTE]
 Cool, create a launcher "gnome-obex-send %u" then just drag and drop files onto it to send them xD

---

### Post by Lord C on 2005-04-21
[IMG]http://usefulinc.com/software/gnome-bluetooth/nautilus-send.png[/IMG] 

We need this.

---

### Post by gbil on 2005-04-21
The Send To mechanism has changed in 2.10 and that is why Send via Bluetooth doesn't work. There is a package nautilus_send_to  (I think that is the name) that creates the Send To menu and in order to add an item to it you must create plugins.

---

