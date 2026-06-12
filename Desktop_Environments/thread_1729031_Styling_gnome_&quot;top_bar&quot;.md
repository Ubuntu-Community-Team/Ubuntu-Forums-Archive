---
title: "Styling gnome &quot;top bar&quot;"
date: 2011-04-14
forum: Desktop Environments
---

### Post by Taus on 2011-04-14
Hi all,

been googling around to find out how this guy made his top menu bar look like this: 

[http://gnome-look.org/CONTENT/content-pre1/140774-1.jpg](http://gnome-look.org/CONTENT/content-pre1/140774-1.jpg)

Does any of u guys know how he managed to do that?

TIA :)

cheers
Taus

---

### Post by TheExposedOne on 2011-04-14
I believe that is 3rd party software not the actual toolbar

That's what it looks like anyway

---

### Post by Frogs Hair on 2011-04-14
With some docks it is possible to add additional docks to the top or side and customize them . It looks like this may be what was done . The Gnome panel may have been replaced with an additional dock.

I use Awn and it has applets for the dock like the Gnome panel including the indicators , notification area , menus , and so on .

---

### Post by Karlchen on 2011-04-14
Hello, guys.

There is less mystery involved than you seem to assume. ;)

[LIST]
[*]Obviously the default wallpaper has been replaced.
[*]The default icon set has been replaced, too.
[*]The upper and the lower Gnome panels have been customized:
[*]Inside the upper and lower panel right-click on some spot which is not occupied by an icon or by a menu item. Select "Properties". Untick [_] *Stretch*. This will make the panel width decrease.
[*]Right-click the menu items "Places" and "System" and select "Remove from panel". This leaves the "Applications" only.
(Perhaps, prior to removing the items from the upper panel, it will be wise to use "System" => "Settings" => "Main Menu" to include "Places" and "System" in the "Applications" menu.)
[*]Right click the clock applet, untick [_] *Fixed panel position*, move the clock applet to the middle of the upper panel and tick [X] *Fixed panel position* again.
[*]In the same way move any panel item to a different position and fix the new position.
[*]Basically that's all.
[/LIST]

Kind regards,
Karl

---

### Post by XsheepX on 2011-04-14
It seems like he has replaced the gnome-panel with another panel. I recall having a very, very similar tint2 panel in Crunchbang. If you really want to get it like that, run gconf-editor, and navigate to desktop>gnome>session>required_components and replace gnome-panel with the panel of your choice (If for some reason it doesn't work, just leave it blank and add the panel's run command to the startup items list.)
I must warn you though: if you replace the gnome-panel, you won't be able to run apps with Alt+F2. You would need to find another way to "run" apps, if you even care. You could always use the terminal, or the .... Menu button on the new panel, lol.

There are lots of alternative panels you could use, but I used tint2. I edited the configuration file to have a panel that was almost exactly like that one. Choose whatever you like.


As for the dock at the bottom, it's just a regular dock, which I can't remember the name, but it's in the Ubuntu repositories.
If the panel at the top really is just an extra dock panel, then you would just have to add the dock to the startup items list and just take out the gnome-panel.

---

### Post by Taus on 2011-04-15
Thank you so much guys for all the good advices! wow! i have some stuff to play around with.

Thanks a lot

btw i think the bottom panel is Docky... looks a bit like it..

i just thougt the top looked really neat

cheers

---

