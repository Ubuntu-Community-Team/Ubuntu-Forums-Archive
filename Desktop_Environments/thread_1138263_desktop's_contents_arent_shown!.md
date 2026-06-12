---
title: "desktop's contents arent shown!"
date: 2009-04-26
forum: Desktop Environments
---

### Post by inman on 2009-04-26
i don't see my desktop's contents on my desktop! the folder desktop exists, but the contained folders and icons aren't shown on my desktop ( on my wallpaper! )! the right click don't work too! any idea?
:confused:

PS. i thought probably the keys on gConfig are inactivated but for the desktop the value " computer_icons_visible " is checked! ( " i mean in Configuration Editor -> /apps/nautilus/desktop/* ... . ) i don't understand why the contained folders in desktop folder are not shown too! ](*,)

---

### Post by drs305 on 2009-04-26
In gconf-editor, in almost the same section, check nautilus/preferences/show_desktop. That setting is the "master" for the desktop and overrides the others if it is not checked.  

Many users have disabled/turned off this setting to allow multiple wallpapers on workspaces, but you lose your desktop icons when you do this.

---

### Post by celticbhoy on 2009-04-26
Are you using compiz wallpaper plugin?

---

### Post by inman on 2009-04-26
> **drs305 said:**
> In gconf-editor, in almost the same section, check nautilus/preferences/show_desktop. That setting is the "master" for the desktop and overrides the others if it is not checked.  

Many users have disabled/turned off this setting to allow multiple wallpapers on workspaces, but you lose your desktop icons when you do this.

sorry, i forgot it to say, it's checked too!

---

### Post by inman on 2009-04-26
> **celticbhoy said:**
> Are you using compiz wallpaper plugin?
i think i do! but can u tell me plz which configuration causes this?

---

### Post by celticbhoy on 2009-04-26
If you are using the compiz wallpaper plugin it covers your icons - just the way it works. If you want to keep it you could try the  folder view applet in screenlets.

---

### Post by inman on 2009-04-26
> **celticbhoy said:**
> If you are using the compiz wallpaper plugin it covers your icons - just the way it works. If you want to keep it you could try the  folder view applet in screenlets.

i think we are on right way! sorry, but i'm not so familiar with ubuntu ( i have used slackware longtime, ...  so how can i deactivate this plug-in?! ) i knew where the copmizConfig is, so i found 2 thing ( maybe plugin as u said before ) , under utilities 'wallpaper' what probably should let me draw a desktop on my wallpaper, and i have somethings called 'desktop wall plugin' under Desktop section in compizConfig. i have deactivated both of them, but it doesnt take efect! any idea? 
tanx!

---

### Post by celticbhoy on 2009-04-26
You have to restart compiz now.

---

### Post by inman on 2009-04-26
> **inman said:**
> i think we are on right way! sorry, but i'm not so familiar with ubuntu ( i have used slackware longtime, ...  so how can i deactivate this plug-in?! ) i knew where the copmizConfig is, so i found 2 thing ( maybe plugin as u said before ) , under utilities 'wallpaper' what probably should let me draw a desktop on my wallpaper, and i have somethings called 'desktop wall plugin' under Desktop section in compizConfig. i have deactivated both of them, but it doesnt take efect! any idea? 
tanx!

i restarted after the changes, you're right it was the wallpaper plugin, i have my deskotp's contents again!
tanx a lot, have a good evening!

---

