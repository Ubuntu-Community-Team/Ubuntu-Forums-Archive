---
title: "Help with a theme/window border issue"
date: 2009-05-24
forum: General Help
---

### Post by Ryoukii on 2009-05-24
Hi i installed Mac4Lin transformation pack and i uninstalled it via the terminal by sudo sh Mac4Lin_Uninstall_v1.0_RC.sh

All went fine and i have my icons back to normal and my themes are fine but the Minimize / close buttons are still on the left hand side and not the right and its getting really really annoying.

Looks like this

[IMG]http://i42.tinypic.com/65pl4z.png[/IMG]

Any idea how to get it back right ?

In themes in window borders it even shows them on the right

[IMG]http://i39.tinypic.com/24ex1yd.png[/IMG]

 but when i apply they still stay on the left :(

---

### Post by Minsky on 2009-05-24
Open a terminal window and type:

**gconf-editor**

In the left hand sidebar of the window that opens, go to **apps > metacity > general**. A list of keys will be displayed in the large pane on the right. Double click on the **button_layout** key and in the small window that appears, type **menu:minimize,maximize,close** in the **Value:** box, and click on **OK** and close the editor. Your buttons should now appear on the right hand side of the window.

---

### Post by Ryoukii on 2009-05-24
Thank you so much its fixed now :D

---

