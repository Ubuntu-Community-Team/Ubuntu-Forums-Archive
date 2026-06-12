---
title: "Desktop icons in Openbox."
date: 2006-10-20
forum: Desktop Environments
---

### Post by paul6 on 2006-10-20
I want desktop icons in Openbox. The wiki page recommends installing Rox-filer. However, to activate the desktop functionality I have to turn on Rox-filer's "pinboard". This is disappointing to me because the Rox-filer pinboard overwrites the Openbox right-click menu with its own right-click menu, which I have spent a lot of time customizing to my preferences.

So is there any alternative to Rox? I really don't want to give up my right-click menu, but I still want desktop icons...

---

### Post by K.Mandla on 2006-10-20
I've not tried this (although I will, since you mentioned it), but the Arch Linux wiki mentions iDesk, which is also in the Ubuntu universe repository. So you can install it through Synaptic, or with *sudo aptitude install idesk*, if you have that repository enabled.

There's more information about it [here]("http://idesk.sourceforge.net/wiki/index.php/Main_Page").

---

### Post by kerry_s on 2006-10-20
Look in rox options and you'll see the option to let right click pass through the desktop.

Okay, i switched over to fluxbox to grab you a pic. The pic shows the option menu where you need to check so the clicks pass thru . So after you start rox pinboard( rox -p=default ), right click the home folder>rox-filer>options>compatiabilty. " rox -p= " to kill rox pinboard.

I didn't bother to put a desktop background cause i don't use desktop icons, so i don't use rox pinboard->

---

### Post by kerry_s on 2006-10-20
Also a little tip for rox pinboard icons. I usally create a folder(Desktop) and in that i make the icon launcher with just a regular text file.

create text file

put this inside->
#!/bin/sh
(appname)

example->
#!/bin/sh
firefox

then right click the text file>and make it executable

then just drag it to the desktop and set a icon on it.

I'm not sure what app's you use but doing it this way instead of grabbing the /bin/executable you can add options to your launcher.

---

### Post by K.Mandla on 2006-10-20
By the way, I tinkered with the iDesk utility this morning, and I really like it. No dependencies, configurable through text files and a cinch to get going. ;) Cheers and thanks for the question! :rolleyes:

---

