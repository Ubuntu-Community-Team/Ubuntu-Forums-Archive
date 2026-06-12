---
title: "How do I change the default gnome panel settings"
date: 2009-10-22
forum: Desktop Environments
---

### Post by Lukios on 2009-10-22
This may be a dumb question but where are the files that handles configuration of gnome panel. I know that you can change things in the .gtkrc-2.0 file, but I want to change the global default settings so that if I were to make a remix cd the gnome panel would be customized with the applets, menus, and colors that I want for it. 

Oh, and I already know about remastersys. It's a great program, but I want to know how to manually edit this myself as well as where the files for the configuration are kept.

---

### Post by mrboojive on 2009-10-22
The files are in your home directory in .gconf/apps/panel/. However, you'd be better off editing them through the gconf-editor than manually. Do Alt+F2, type "gconf-editor" and then use the left pane to navigate to apps > panel.

---

### Post by Lukios on 2009-10-22
I looked there, but I don't see anything that would specifically allow me to edit exactly what applets and menus I want where. Can you give me a couple examples or point me in the right direction? Thanks.

Also I want the global settings, not the user settings.

---

### Post by mrboojive on 2009-10-22
Under panel/applets there are a number of folders called applet_0, applet_1, mixer, etc. There is one for each applet on the panel. On the right side in gconf-editor it shows the options for the applets. For example, it has keys and values for "toplevel_id" which is the panel that the applet is on and "position" which is the position on the panel in pixels.

I think the global panel settings that are applied to every new user are located in an XML file called panel-default-setup.entries in /etc/gconf/schemas/.

All that said, I don't know much about creating remixes, but there's probably an easier way than editing all of these files manually.

---

### Post by Lukios on 2009-10-22
> **mrboojive said:**
> I think the global panel settings that are applied to every new user are located in an XML file called panel-default-setup.entries in /etc/gconf/schemas/.


Yeah, I just found that a few minutes ago. One thing I did not do was look specifically at the applets in gconf-editor, but now I see exactly what you were saying. Thanks for all your help, this should help me get the job done.

---

