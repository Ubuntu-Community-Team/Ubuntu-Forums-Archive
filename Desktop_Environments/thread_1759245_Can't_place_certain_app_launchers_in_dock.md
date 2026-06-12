---
title: "Can't place certain app launchers in dock"
date: 2011-05-15
forum: Desktop Environments
---

### Post by Pahanilmanlintu on 2011-05-15
Some app launchers can't be placed in the dock. The ones i have trouble with are the three games from Humble Frozenbyte Bundle, namely Shadowgrounds, Shadowgrounds Survivor and Trine. Their launcher icons look fine on dash, but when i start dragging them and the dash disappears, the icon turns into a question mark. Items on dock make room for the question mark icon, but after dropping it, it disappears and the dock icons return to where they were.

I guess there's something non-standard about the launchers. The games are installed under my home folder, and the game icons are xpm files in the game folder, like /home/veepee/.trine/Trine.xpm for example. The executables are in the same folder, like /home/veepee/.trine/trine-bin.

Too bad the print screen key doesn't take screenshots when the dash is up. What's up with that anyway?

---

### Post by Frogs Hair on 2011-05-15
When you open the application if the icon appears on the panel right click and select "keep in launcher".

If the icon does not appear in the panel I don't know what the next step would be .

---

### Post by Pahanilmanlintu on 2011-05-15
Oh man. I feel stupid, it was as simple as that.

Although the actual problem is still there, as in, some icons can't be dragged to the dock, but that's probably more a place for a bug report.

---

### Post by NormanFLinux on 2011-05-16
If you know how to create desktop. configuration files, open up gconf-editor, head to desktop, then unity, then favorites key and add your application there. After you click OK and close the menu, you will have to logout and login again to see your application appear in the launcher.

---

### Post by cybergalvez on 2011-05-16
> **Pahanilmanlintu said:**
> Oh man. I feel stupid, it was as simple as that.

Although the actual problem is still there, as in, some icons can't be dragged to the dock, but that's probably more a place for a bug report.

Just use the old menu editor to create an entry for them in the menu, they will then be in Dash and can be dragged to the launcher

---

