---
title: "Icons missing from Desktop"
date: 2005-03-29
forum: Desktop Environments
---

### Post by cantas on 2005-03-29
Hi,
I just decided to reinstall the whole ubuntu system.
So I installed it from warty and then upgraded to hoary.
After upgrading, Home and trash icons have disappeared from the desktop, even though they still appear in the /home/stefano/Desktop folder.

I tried deleting my user ecc ecc but nothing seems to work. Can anybody help me?

Thanx
Stefano

---

### Post by apokryphos on 2005-03-29
Yes, that's the default on Kubuntu. You need to merely make links on the Desktop; Right-Click > Create New > Link to Location. Good as new.

---

### Post by cantas on 2005-03-29
Ugly... why shouldn't one want a trash icon on its Desktop by default?
Now I try your suggestion, even though I tried it before but I couldn't set the correct icons for the trash...

Thank you!
Stefano

---

### Post by cantas on 2005-03-29
I found a more obvious and wiser solution.
Just open with a text editor the trash.desktop file in your Desktop/ directory and toggle Hidden=true with Hidden=false. Restart KDE and it's done.

Stefano

---

### Post by Randabis on 2005-03-29
[QUOTE=cantas]Ugly... why shouldn't one want a trash icon on its Desktop by default?
Now I try your suggestion, even though I tried it before but I couldn't set the correct icons for the trash...

Thank you!
Stefano[/QUOTE]
 I don't like any icons at all on my desktop so go figure.

---

### Post by Cmykus on 2005-03-29
[QUOTE=cantas]Ugly... why shouldn't one want a trash icon on its Desktop by default?
Now I try your suggestion, even though I tried it before but I couldn't set the correct icons for the trash...

Thank you!
Stefano[/QUOTE]


work :


Right-click on an empty place on your desktop.
Select "Create New" > "Link to Location (URL)"

When that window opens fill in the following information:

File Name: Trash
Enter Link To Location (URL): trash:/

Click okay. That should set you back up.
The normal icon should appear in your next session.

---

