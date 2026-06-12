---
title: "gnome / lost bottom taskbar"
date: 2009-03-03
forum: Desktop Environments
---

### Post by raymondh on 2009-03-03
Lost the bottom taskbar/panel.  Tried sudo apt-get install gnome panel.  Also made sure gconf-editor > app>nautilus> panel is checked.  Tried to "add a panel".  However, when I minimize a program, I got used to seeing the app on the bottom left ...which I cannot recreate now with this new, added panel.

Any tips on how to get back my old desktop without any need to do a clean re-install?

Thanks in advance.

---

### Post by Tamlynmac on 2009-03-03
Not quite sure I understand. 

Missing panel: If you have a top panel right click on your panel and left click on "New Panel" Make sure new panel is at bottom - if not click and drag it to the bottom.

Once your panel is at the bottom - right click on the panel and say "add to panel". A menu will open and from the menu select "Window List". Left click on the "add button".

Now when you minimize the window it will appear at the bottom panel.

You can use "Window List" for the top panel if you choose, with the same procedure as above. But if you have two panels only one will show the minimize button.

One additional thing to check is:

Make sure in you config-editor that
apps/panel/global/ lock_down is not checked. If so uncheck it. Or the install "new panel" will not work. Nor will you be able to move anything in the panel.

Hope this helps.

---

### Post by MaryJaneBg on 2009-08-20
special thanks and from me, this helped me a lot, i lost my task bar and it was so easy to recover it :D

---

### Post by Tamlynmac on 2009-08-20
I had forgotten all about this assistance request. I'm very glad you found it helpful.

Mac

---

