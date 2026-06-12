---
title: "Hoary and removing Gaim"
date: 2005-03-13
forum: Desktop Environments
---

### Post by marcadams on 2005-03-13
Hello;

Just installed Hoary preview, and tried to remove GAIM from via Synaptic.
The package was removed, but the menu item remains (if I now click on the menu item, I get a 'no such file or process' message)

How can I manually remove this item from the menu?

Many thanks
Marc

 #-o

---

### Post by marcadams on 2005-03-17
Anybody have any suggestions?

Where is the menu structure stored on Linux - if I know I can manually remove the item

Thanks
Marc

---

### Post by IdoMcFly on 2005-03-17
maybe there is a gaim-gnome package or something like this?

---

### Post by rudiz on 2005-03-17
Reboot.

---

### Post by darrenadams on 2005-03-17
Nothing as drastic as a reboot is required here. Simply logging out then logging back in should remove the Gaim item.

If you really don't want to do that, then you open a terminal and type 'killall gnome-panel' (assuming you're using GNOME here, you never said..) and when the panel restores itself, the item should be gone

---

### Post by KLineD on 2005-03-17
And if all of that fails, check out the /usr/share/applications directory to see if there's a gaim.desktop file. If there is one indeed, delete it.

---

### Post by cutOff on 2005-03-17
[QUOTE=KLineD]And if all of that fails, check out the /usr/share/applications directory to see if there's a gaim.desktop file. If there is one indeed, delete it.[/QUOTE]
Yes, it's the better way for me.


Regards

cut0ff

---

### Post by marcadams on 2005-03-18
I have removed the GAIM package via synaptic, and rebooted many times since then.

I think the packaged just did not remove the item from the menu when uninstalled - and as there does not seem a GUI interface to remove the item manually, I thought someone more knowledgeable could help....which is not too hard  :) 

Anyhow I will investigate the "/usr/share/applications" directory and look for a  "gaim.desktop" file.

Thanks for all your help,
Marc

---

### Post by marcadams on 2005-03-18
Thanks KLineD - removing the gaim.desktop file did the trick.

Thank-you all for your help
Marc

---

### Post by KLineD on 2005-03-18
No problem glad I could help.
Cheers!

---

