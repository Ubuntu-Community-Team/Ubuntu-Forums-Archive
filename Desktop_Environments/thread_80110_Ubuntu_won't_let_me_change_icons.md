---
title: "Ubuntu won't let me change icons"
date: 2005-10-21
forum: Desktop Environments
---

### Post by darknuala on 2005-10-21
When trying to create a custom launcher, or change the icons I am running into problems.  Of course the default location is usr/share/pixmaps.  I have a folder in my home directory called icons, where I keep alot of the ones I've downloaded.  Whenever I browse to change the icon to something other than what is in usr/share/pixmaps, the icons are "greyed" out, and it will not let me select any of them.  I've tried copying the folders to different locations, and no change.  The same thing happens in gdesklets, whenever I try to create a starter bar, it will only let me choose the icons that are in usr/share/pixmaps.   Does anybody have any ideas?

---

### Post by GrumpyBob on 2005-10-21
Presumably you can copy icons to usr/share/pixmaps (you might need sudo to do it), and then change icons...

Robert

---

### Post by objorkum on 2005-10-21
You have to browse to the exact folder that holds the icon file you want to use.

BTW: Put icon-themes in /usr/share/icons (system-wide) or ~/.icons (user). Then you can choose to use icon-themes in the Theme-changer.

---

### Post by darknuala on 2005-10-21
Thanks, I'll try that and see if it works.  I'll try copying the icons to /usr/share/pixmaps.  browsing to the exact folder of the icons, still won't let me change them.  I'll let you know how it works.

Thanks,

---

### Post by kperkins on 2005-10-31
I'm having this same problem.  If I want to change an icon on gnome-panel, and right-click to go to properties, and click on the icon it opens the folder that the icon is from (the following happens no matter what folder the icon was in), when I change folders using the browse button, I can't choose any icons in any folder.

Has anyone got a fix for this yet?

---

### Post by kperkins on 2005-10-31
OK so it's this bug.
[http://bugzilla.gnome.org/show_bug.cgi?id=310288](http://bugzilla.gnome.org/show_bug.cgi?id=310288)
also seen here:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=13208](https://bugzilla.ubuntu.com/show_bug.cgi?id=13208)
Very user unfriendly, and counter-intuitive.

---

### Post by RawMustard on 2005-10-31
This seems to have been fixed in Breezy final, which version are you using?

Anyway, you can just drag your favourite icon from its folder onto the icon button and it should stick :)

---

### Post by kperkins on 2005-10-31
Breezy final.
It's actually a Gnome bug (and there is a "workaround"). 
Thanks for the tip about the DnD, but that's still really not very userfriendly, or intuitive.  You have to open up properties and a file browser, not really optimal.

---

