---
title: "Desktop Icons Gone Upon Boot, Back When Nautilus Called"
date: 2009-10-20
forum: Desktop Environments
---

### Post by Gias Kay on 2009-10-20
Hello all,

This problem has been haunting me since I upgraded from Intrepid to Jaunty. I figure it's time to find a solution for it before I advance into Karmic.

At first (immediately after the upgrade), I lost my Metacity shortcut to open up a new nautilus window. Then someone instructed me to use CompizConfig Settings Manager and enable the General &#8594; Commands option. It worked.

But it turned out to be that, everytime when I start Ubuntu, icons on my desktop will not show up. I will have to manually open a nautilus process to "call up" the desktop icons.

I suspect it's something between Metacity & Compiz settings never working perfectly, but I have the least of the clue on how to fix it.

So if anyone knows of a solution, please help me. Thanks.

---

### Post by undecim on 2009-10-20
Press ALT+F2 and type "gconf-editor"

When the Configuration Editor opens, in the left side of the window, navigate to /desktop/gnome/applications/session. In the right side of the window, find the "required_components_list" key and make sure that its value contains "filemanager" (example: "[windowmanager,panel,filemanager]")

Then in  /desktop/gnome/applications/session/required_components, make sure that the "filemanager" key is set to "nautilus"

---

### Post by Gias Kay on 2009-10-21
Hi,

Thanks for the reply :)

But what you suggested is already the case in my configuration.

/desktop/gnome/session/required_components_list
**[windowmanager,panel,filemanager]**

/desktop/gnome/session/required_components/filemanager
**nautilus**

/desktop/gnome/session/required_components/panel
**gnome-panel**

/desktop/gnome/session/required_components/windowmanager
**compiz**

Furthermore, my
/apps/nautilus/preferences/show_desktop
is **checked**.

And despite all these I am have the problem.

---

