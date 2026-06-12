---
title: "Unity Launcher on top of Gnome Shell"
date: 2012-06-01
forum: Desktop Environments
---

### Post by OakRaider4Life on 2012-06-01
I'm in a bit of a pickle with my Ubuntu desktop environments. I like the Unity launcher/dash (and the panel, but only b/c of its applets), but I like the Gnome panel more, and I like the gnome notification system. So the ideal solution for me would be to add a Unity launcher to Gnome 3, and I would have the best of both worlds (I can live without the dash). 

So we come to my question. Does anyone know of a way to get a Unity launcher working in Ubuntu 12.04 with Gnome Shell? I've read a couple solutions, but they were optimized for the 11.* releases.

---

### Post by dniMretsaM on 2012-06-01
> **OakRaider4Life said:**
> I'm in a bit of a pickle with my Ubuntu desktop environments. I like the Unity launcher/dash (and the panel, but only b/c of its applets), but I like the Gnome panel more, and I like the gnome notification system. So the ideal solution for me would be to add a Unity launcher to Gnome 3, and I would have the best of both worlds (I can live without the dash). 

So we come to my question. Does anyone know of a way to get a Unity launcher working in Ubuntu 12.04 with Gnome Shell? I've read a couple solutions, but they were optimized for the 11.* releases.

You might look at [this](http://www.omgubuntu.co.uk/?p=57933).

---

### Post by OakRaider4Life on 2012-06-01
I have viewed the aforementioned post, but Bolt is a buggy implementation of the dash which doesn't include lenses, the key feature which makes the unity dash perferable. Mostly, I'm concerned with trying to find a way to add a Unity launcher to Gnome shell.

---

### Post by renearts on 2012-07-23
I may have a solution for you! Look at these screenshot's, I think it's close to your (and mine) ideal DE. I run 12.04, btw :)

[[img]http://imgbin.org/images/thumbs/ext8757.png[/img]](http://imgbin.org/index.php?page=image&id=8757)

[[img]http://imgbin.org/images/thumbs/ext8756.png[/img]](http://imgbin.org/index.php?page=image&id=8756)

I've altered the unity-2d launcher (deleted dash buttonm, workspaces and removable drives) and started it within gnome-shell. Works great! 
Only one small disadvantage; the HUD doesn't work. The dash is usable though don't know if it reacts to pressing the Super key as I removed it. I really love the dynamic workspaces from gnome-shell, that's what made me decide to switch. But I also love the Dash/HUD and Unity panel (mainly because of the global menu) and launcher. 
Another tweak (extension) I did to gnome-shell was removing the gnome-shell application launcher/favorites since I now have the Unity launcher :)
 
[here some info about the changes I made to /usr/share/unity-2d/shell/launcher/Launcher.qml]("http://gathering.tweakers.net/forum/list_message/38583320#38583320")
If you (or others) need some more info or a more detailed translation please let me know :)

---

### Post by renearts on 2012-08-02
Hey there, I'm back again with some new improvements... I've managed to get the HUD to work :) Looks and works great!
I brought back the Unity Dash button on the Launcher and altered some key mappings so the Dash shows up when pressing Super/Win key. The GS activities overview is only triggered with Alt-F1 or going to the hot corner with the mouse. Here's how it looks:

With Dash:
[[img]http://imgbin.org/images/thumbs/ext8975.png[/img]](http://imgbin.org/index.php?page=image&id=8975)


and the HUD at work: 
[[img]http://imgbin.org/images/thumbs/ext8976.png[/img]](http://imgbin.org/index.php?page=image&id=8976)

IMHO the Dash and HUD even look better with the transparent GS panel than with the Unity panel :-D

To get the HUD to work, just add /usr/lib/unity/unity-panel-service to your startup applications. Little warning; the menu bar will be hidden when running this process, but that's exactly where the HUD is meant for... :)

---

### Post by OakRaider4Life on 2012-08-10
Wow this looks like great work! I don't have Ubuntu on my system currently, but I will definitely restore my 12.04 install just to give this desktop a whirl!

---

### Post by renearts on 2012-08-10
It's not hard, first add the next commands to your startup list (I think you guys should know how to do that...)
For the Unity launcher: unity-2d-shell
To get the HUD working: unity-panel-service 
sidenote: when you start unity-panel-service, the menu bar will be removed from your application windows; but off course the HUD's purpose is to replace it ;)

In this configuration the Dash (and icon) is still present in the launcher: I like it this way, with both Dash and HUD and disabled the Gnome Shell Activities overview being triggered with the Super key.
If you don't like the Dash icon on your launcher you can disable it:
- open a terminal window
"sudo gedit /usr/share/unity-2d/shell/launcher/Launcher.qml"
- scroll towards the end of this file
Search for and edit the next section:
```
Component.onCompleted: {
        items.appendModel(bfbModel);
        items.appendModel(applications);
        /* items.appendModel(workspaces); */
        /* items.appendModel(devices); */
        shelfItems.appendModel(trashes);
}
```

commenting out the lines with:
bfbModel removes the Dash
workspaces removes the workspaces button
devices removes the removable drives icons 
trash removes the trash button (doh!)
I suggest leaving applications uncommented :grin:
Save the changes and restart (don't know if restarting just GS is enough, log out and back in to be sure).

That should do it :) 
Good luck and enjoy!

---

### Post by nikander on 2012-10-17
> **renearts said:**
> It's not hard, first add the next commands to your startup list (I think you guys should know how to do that...)
For the Unity launcher: unity-2d-shell
To get the HUD working: unity-panel-service 
sidenote: when you start unity-panel-service, the menu bar will be removed from your application windows; but off course the HUD's purpose is to replace it ;)

In this configuration the Dash (and icon) is still present in the launcher: I like it this way, with both Dash and HUD and disabled the Gnome Shell Activities overview being triggered with the Super key.
If you don't like the Dash icon on your launcher you can disable it:
- open a terminal window
"sudo gedit /usr/share/unity-2d/shell/launcher/Launcher.qml"
- scroll towards the end of this file
Search for and edit the next section:
```
Component.onCompleted: {
        items.appendModel(bfbModel);
        items.appendModel(applications);
        /* items.appendModel(workspaces); */
        /* items.appendModel(devices); */
        shelfItems.appendModel(trashes);
}
```

commenting out the lines with:
bfbModel removes the Dash
workspaces removes the workspaces button
devices removes the removable drives icons 
trash removes the trash button (doh!)
I suggest leaving applications uncommented :grin:
Save the changes and restart (don't know if restarting just GS is enough, log out and back in to be sure).

That should do it :) 
Good luck and enjoy!
I try to make this desktop, but i have some problems.
How did you remove gnome-shell application launcher/favorites from gnome shell? And how did you remove window menu?

---

