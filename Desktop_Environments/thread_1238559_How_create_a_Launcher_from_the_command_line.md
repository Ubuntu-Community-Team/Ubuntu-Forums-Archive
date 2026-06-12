---
title: "How create a Launcher from the command line"
date: 2009-08-12
forum: Desktop Environments
---

### Post by nbrinson on 2009-08-12
I need to write a script that will create several desktop launchers so our user don't have to create them manually.  Is there a command to do this?

---

### Post by warp99 on 2009-08-12
Long story short, no command to do this. But you can make a simple script that can do this using a *.desktop file layout. What exactly do you want your users to do?

---

### Post by nbrinson on 2009-08-12
Thanks for the reply.
 
I'd like to create a script that will place the following luancher on the desktop of several computers....
 
The launcher should point to this command:  **/usr/bin/ibm5250 as400.mydomain.com -sso**
and it will have this icon:  **/usr/share/pixmaps/tn5250-48x48.png**
 
I have several other launchers that I'd like to add as well.

---

### Post by VCoolio on 2009-08-12
Just make the .desktop files in a text editor and copy them to the users desktops, wouldn't that be easier? The .desktop files are like this (there are more options, but this should do:

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Name=Whatever name you want
Comment=Whatever comment you want in the tooltip
Exec=/usr/bin/ibm5250 as400.mydomain.com -sso
Terminal=false
Type=Application
Icon=/usr/share/pixmaps/tn5250-48x48.png
```

You can also place the launcher in ~/.local/share/applications, add a line like "Categories=Office;" and it will show up in the applications menu under 'Office' (after restarting the gnome-panel).

---

### Post by warp99 on 2009-08-12
VCoolio is correct. If you have the computers networked users can drop and drag the desktop launchers from the remote share, which would be much easier then a script.

---

### Post by nbrinson on 2009-08-13
That'll work... Thank you!

---

