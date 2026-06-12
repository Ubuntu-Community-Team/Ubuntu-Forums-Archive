---
title: "How to change menu/settings for all users?"
date: 2005-07-28
forum: Desktop Environments
---

### Post by pesachzon on 2005-07-28
Hi,
I just installed 3.4.2.
How can I add kcontrol to the menu of all users and not just the one logged in?

thanks

---

### Post by SGC on 2005-07-28
**The short answer:**

Create a link to the control center in  /usr/share/applnk


**The long answer:**

Open this folder:
/usr/share/applnk

Right click inside the folder and choose "Create new" -> "Link to Application..."

Change the application name to "Control Center" and change the icon from the General tab.

In the application tab, type **kcontrol** in "command" field

---

