---
title: "Lost gnome panel transparency on upgrade to 10.04"
date: 2010-07-25
forum: Desktop Environments
---

### Post by Jack.Straw on 2010-07-25
Hello.  I recently upgraded from 9.04 to 10.04 and things went pretty smooth.  The only real issue is that I lost the transparency settings for the menu & indicator applets on my top knome panel.  I simply don't remember how i did it last time, and i've been searching the net for an hour for a solution with no luck.  Many results suggested the use of the Compiz Settings Manager's opacity settings, but that opacity applies to everything, including the text & icons.  I thought i used the "gnome color chooser" package to do it last time, but I cannot find the option in the gui. Can anyone tell me how to make the background of the menu (applications/places/system) and indicator applet have transparent backgrounds while retaining full text/icon brightness?

[IMG]http://olfactoryhues.com/temp/opacity.png[/IMG]

Thanks for your time,
-Scott

---

### Post by Jack.Straw on 2010-07-26
El bumpo :)

---

### Post by mcduck on 2010-07-26
You need to remove the panel theming from your GTK theme.

Whatever the GTK theme defines as background image/color for panel applets will override whatever you try to set directly from the panel's options. Once you remove panel theming from the GTK theme the panel and everything inside it will respect the background you set for the panel itself.

Most new GTK themes have a separate panel.rc -file. In that  case removing/renaming that file will do the trick: If there isn't such file you just need to go through the main theme file and search for anything panel-related & comment it out.

---

### Post by Jack.Straw on 2010-07-26
That did it, thanks for your help!

---

