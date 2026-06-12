---
title: "Title bar hidden"
date: 2009-04-24
forum: General Help
---

### Post by xyZen on 2009-04-24
Morning all,

Since doing the jaunty update last night, whenever i open an application, it appears in the top left hand corner of my desktop, with the title bar (carrying the close/minimise/maximise buttons etc) obscured so i cant move the window around.

Having done some light googling on the subject, i have a workaround- being to change my desktop backround from one image to another- this causes the windows to re-size and show the title bar again- however when i restart the machine, the problem is there again.

Has anyone got any ideas as to a more permanent fix?

Many thanks in advance...

---

### Post by Peter09 on 2009-04-24
Sort term - you can move the window by holding the ALT key and using the mouse.

Try going into System->Preferences->CompizConfig Settings

and go to the WINDOWS MANAGEMENT tab and making sure that PLACE WINDOWS is ticked and in there the Placement mode is set to SMART.

Note - you may need to install Compiz Manager

---

### Post by xyZen on 2009-04-24
> **Peter09 said:**
> Sort term - you can move the window by holding the ALT key and using the mouse.

Try going into System->Preferences->CompizConfig Settings

and go to the WINDOWS MANAGEMENT tab and making sure that PLACE WINDOWS is ticked and in there the Placement mode is set to SMART.

Note - you may need to install Compiz Manager

i was trying to move the windows when holding downt he alt key, and it wasnt working, but ill try the Comiz settings, cheers :)

---

### Post by mcduck on 2009-04-24
Actually that sounds more like you just don't have any window manager running.

Try one of these commands, they should get your window frames back (and allow moving windows etc.):

Gnome's default window manager (no desktop effects):
```
metacity --replace
```

Compiz (desktop effects):
```
compiz --replace
```

The first one should work in all cases, the last one works if you have properly working drivers for your graphics card. If you were using Compiz before the update it could be that the drivers are not working correctly now which caused Compiz to fail and your window frames to disappear. If that's the case you should first set the desktop effects to "none" (to make Metacity the default window manager and start it automatically on login), and then try fixing the driver problem. How to do that of course depends on what graphics card you have and what kind of drivers you are using for it.

---

### Post by xyZen on 2009-04-24
ah ha- will give that a try, thanks very much.

if it's of any help, the card is a ATI 4650, and im running the latest version of catalyst...

---

