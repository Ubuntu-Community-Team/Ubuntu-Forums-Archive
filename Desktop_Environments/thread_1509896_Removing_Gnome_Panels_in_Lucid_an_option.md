---
title: "Removing Gnome Panels in Lucid an option?"
date: 2010-06-14
forum: Desktop Environments
---

### Post by slipknott on 2010-06-14
Hello, 

I am interested in removing the gnome panels from my desktop in 10.04.  I know i can auto-hide the top and bottom panels and there is also an option to delete them. When they auto-hide a small white line is still visible and i accidentally hover over them sometimes briefly showing them also. I also do not want to do anything permanent like deleting them.

In some past forum posts i saw people saying go to System>Preferences>Sessions but this option seems to be missing in lucid and these seem to be for slightly older versions on ubuntu. I then added the gnome-session-properties command in the Edit Menu... of System but all it did was launch Startup Applications.  One post i saw said to go into Sessions, required sessions and make it empty.  Should this work like i want it too and if so, is there an option like this still in Lucid. I basically want to remove the panels completely from my desktop, but still want to be able to bring them back if i want too also (Hopefully without having to edit them again, but i can live with it if i do).

Thanks!,
Slip

---

### Post by Breambutt on 2010-06-14
You can hide them on the widget layer with compiz and make them visible with F9 (default key).

```
sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-extra
```

Just add *class=Gnome-panel* in the empty field under the Behavior tab inside the Widget Layer options.

Edit: Not sure about the name of the lower panel as I'm using Studio, but you can grab the panel information with a simple point'n'click crosshair tool.

---

### Post by slipknott on 2010-06-15
Just tried it and it's working like a champ, thanks! :)

---

### Post by raditzman on 2010-07-27
Could you please explain me where exactly do I do those changes (what app, and inside which settings), since I'm also trying to get rid of the top panel.

Thank you so much.

---

### Post by amurillo on 2010-08-22
Go to "Preferences->CompizConfig Settings Manager"

Filter or find "Widget Layer"

Go to "Behaviour" tab

Edit Widget Windows field, set it to "class=Gnome-panel"

Check "Enable Widget Layer"

That should do it.

---

