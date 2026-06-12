---
title: "Trash can links to Music Folder"
date: 2011-05-11
forum: Desktop Environments
---

### Post by Dem_z on 2011-05-11
I'm getting strange shortcut linking problems... I don't create shortcuts, but the existing ones seem to randomly relink, or break... Is there any sort of permission repair that I can do? Or Shortcut repair? 

I tried searching to no-avail. Thought I'll have better luck here :).

---

### Post by Paddy Landau on 2011-05-11
I think you will have to be specific. Which existing shortcuts? What happens when you click on them? Where are the links -- in your home folder, on a USB stick, somewhere else? Does it happen when you log in normally? What system are you using -- WUBI? Ubuntu 10.04? 11.04? Something else?

Remember that we can't see your computer screen, so you need to be explicit.

---

### Post by Dem_z on 2011-05-11
Sorry. On 11.04. Left default sidebar, I click on the trash icon, and it opens up music player.

---

### Post by Paddy Landau on 2011-05-11
Hmm, that is odd. I'm sorry, I don't know Unity well at all. Let's hope someone else with more experience can help.

---

### Post by Dem_z on 2011-05-11
yah it's pretty weird. If there's any way that I can configure the shortcut, that'll be a big help.. I can view the trash can from the homefolder's sidebar... But not unity's launcher.. The launcher's right click option is "empty trash"... 

Is there a way to just reinstall the unity launcher bar?

---

### Post by Krytarik on 2011-05-11
Check the specifications in "~/.local/share/applications/mimeapps.list" and remove the respective faulty line.

Greetings.

---

### Post by Dem_z on 2011-05-11
> **Krytarik said:**
> Check the specifications in "~/.local/share/applications/mimeapps.list" and remove the respective faulty line.

Greetings.

Awesome thanks!.. But i'm afraid of editing things I'm not really totally aware of... I don't see anything that's related to the 'trash' icon.

This is what's in the mimeslist file:
```

[Added Associations]
x-content/audio-player=rhythmbox.desktop;
application/x-ms-dos-executable=wine.desktop;totem.desktop;
application/x-rar=gnash.desktop;firefox.desktop;
application/x-extension-drive=hornsey.desktop;nautilus-browser.desktop;evince.desktop;gnome-appearance-properties.desktop;vlc.desktop;nautilus-folder-handler.desktop;azureus.desktop;
application/x-extension-SYS=rhythmbox.desktop;
inode/directory=rhythmbox.desktop;nautilus-browser.desktop;nautilus-autorun-software.desktop;
application/x-msi=wine.desktop;
application/x-extension-IFO=brasero.desktop;
```

---

### Post by Krytarik on 2011-05-11
I guess the responsible line is those of "inode/directory" (although that wasn't used to be the case until Natty), but since there other faulty entries as well, I recommend purging the entire file. ;-)

---

### Post by mc4man on 2011-05-11
I would also say delete mimeapps.list and see.

It is ok and normal to now have an inode/directory= line with app desktops listed in the [Added Associations] section
This just makes those apps immediately available from the r. click on a folder
Ex. mine
inode/directory=vlc.desktop;audacious2.desktop;totem-xine.desktop;


In the [Default Applications] section the inode/directory= , if there, should never have anything other than your file manager (typically nautilus
Ex. mine
inode/directory=nautilus-folder-handler.desktop

---

