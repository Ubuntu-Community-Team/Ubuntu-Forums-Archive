---
title: "beryl-manager icon gone from gnome-panel"
date: 2007-03-16
forum: Desktop Effects &amp; Customization
---

### Post by svenole on 2007-03-16
Ubuntu 6.10, NVIDIA on Dell D620 laptop. The beryl icon has disappeared from the gnome-panel and it does not appear on the add-to-panel in preferences. How can that be? How can I get it back??

---

### Post by mcduck on 2007-03-17
Do you still have the Notification Area-applet in your panel? If not, add it to your panel.

If you have that applet but still can't see the Beryl icon try running 'beryl-manager &' from a terminal.

---

### Post by svenole on 2007-03-17
> **mcduck said:**
> Do you still have the Notification Area-applet in your panel? If not, add it to your panel.

If you have that applet but still can't see the Beryl icon try running 'beryl-manager &' from a terminal.

This did the trick. However it created a new question. What is the difference between running "beryl manager" and "beryl-manager"?

---

### Post by old_geekster on 2007-03-17
Assuming that you are talking about in "Applications/System Tools", from what I could tell --- nothing.

I actually deleted Beryl-Manager.  It didn't seem to cause any problems for me.  I have Beryl Manager in the "Startup Programs", so it loads at boot.

---

### Post by mcduck on 2007-03-18
> **svenole said:**
> This did the trick. However it created a new question. What is the difference between running "beryl manager" and "beryl-manager"?

There is no program called 'beryl manager', the name for the program providing the icon is 'beryl-manager'. The 'Beryl Settings Manager' you see in the menus is 'beryl-settings'.

---

