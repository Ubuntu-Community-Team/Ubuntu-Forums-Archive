---
title: "Does anyone know how to customize the &quot;main menu&quot;"
date: 2007-11-23
forum: Desktop Effects &amp; Customization
---

### Post by kdarkentity on 2007-11-23
What i am trying to do is this, i would like to change the default ubuntu logo for the main menu to a vista logo and also i was wondering if there was a way i could add a live search bar into the popupmenu as well.

---

### Post by 4KvRMU7Nnv on 2007-11-23
its not possible with the default gnome menu.  If you use KDE, there are a couple of menu replacements with this functionality.  Also, for gnome there are a couple of things that I believe do this sort of thing.  Maybe the Suse Sled menu.  Its available for ubuntu i think from the repos.  The app "Gimmie" might also so something similar.  As for changingin the icon, if you're not using the menu bar and just the plain menu button, you can change it by going into "gconf-editor"  Apps>Panel>Objects>object_x and then check the box that says "use custom icon" and fill in the path to the custom icon in the custom icon section.  hope this helped.!

---

### Post by kdarkentity on 2007-11-23
> **d3br074 said:**
> its not possible with the default gnome menu.  If you use KDE, there are a couple of menu replacements with this functionality.  Also, for gnome there are a couple of things that I believe do this sort of thing.  Maybe the Suse Sled menu.  Its available for ubuntu i think from the repos.  The app "Gimmie" might also so something similar.  As for changingin the icon, if you're not using the menu bar and just the plain menu button, you can change it by going into "gconf-editor"  Apps>Panel>Objects>object_x and then check the box that says "use custom icon" and fill in the path to the custom icon in the custom icon section.  hope this helped.!

I dont have an object-x is it object-0?

---

### Post by kdarkentity on 2007-11-23
Gimmie is cool but i dont think its what im looking for. I looked for suse sled in synaptic but didnt see it could you show me where to get it

---

### Post by GameKing505 on 2007-11-23
The icon thing is easy. You just go into your themes folder, look for human, and go to the 22x22 icons. Replace the start-here.png with the icon that you want to be the new logo. Then just run the command killall gnome-panel and it should work.

---

### Post by kdarkentity on 2007-11-24
only thing is i cant seem to remember how to copy an image and change directory and paste, i would need to do this so i could paste the custom logo in the themes directory

---

