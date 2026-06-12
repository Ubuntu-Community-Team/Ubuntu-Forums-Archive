---
title: "Customize Cursor Theme"
date: 2012-01-27
forum: Desktop Environments
---

### Post by surenot on 2012-01-27
So I followed the instructions from the following website on how to create one's own cursor:  [http://www.ehow.com/how_5026012_make-cursors-file-ubuntu.html](http://www.ehow.com/how_5026012_make-cursors-file-ubuntu.html)  It worked, and I have my custom cursor.  Unfortunately, it doesn't give any instructions on how to get Ubuntu to use that cursor.  Anyone know how, or should I just use "sudo mv" on terminal to replace the 'arrow' file in a given pre-installed cursor theme directory?

---

### Post by stinkeye on 2012-01-27
This is for 11.10.
Put your cursor theme into **/usr/share/icons** or **~/.icons** 
then run these two commands using [COLOR="darkorchid"]your cursor theme name[/COLOR].
You need to log out/in to complete.
```
gsettings set org.gnome.desktop.interface cursor-theme "[COLOR="DarkOrchid"]ThemeName[/COLOR]"

sudo sh -c "echo '[Icon Theme]\nInherits=[COLOR="darkorchid"]ThemeName[/COLOR]' > /usr/share/icons/DMZ-White/cursor.theme"
```

You can change back to default with 
```
gsettings set org.gnome.desktop.interface cursor-theme "DMZ-White"

sudo sh -c "echo '[Icon Theme]\nInherits=DMZ-White' > /usr/share/icons/DMZ-White/cursor.theme"
```

---

### Post by lolpenguin on 2012-01-27
Or use Advanced Settings (apt-get install gnome-tweak-tool) instead of gsettings.

---

### Post by surenot on 2012-01-28
Okay, I will try those and see if they work.  Another question, I'm a tad curious as to how to file the cursor theme.  The instructions only told me how to make the X11 cursor file, and nothing else.  So should the path be something like /usr/share/icons/mycursor/cursor/default, or /usr/share/icons/mycursor/default, or simply /usr/share/icons/default ('default' being the name of the X11 cursor file itself).  And if it is like /usr/share/icons/mycursor....  are there other files that have to be in there?

---

### Post by stinkeye on 2012-01-28
Put it in the same format as other cursor themes.
eg I downloaded the Pulse-Glass cursor theme and it appears as in pic.
The cursor images are in the **Pulse-Glass/cursors** folder.

---

### Post by gandalf3 on 2012-09-14
I tried just replacing the "arrow" X11 file in "DMZ-White" to see if it would work. (it didn&#8217;t)
and not even when i installed pulse glass did anything change.. :confused:

i restarted, logged out/in etc.. but nothing worked. i tried changing the to pulse glass from the default with alternatives and lxapperance but neither worked.

the cursor DID turn black and smaller, except when it was in Firefox, ans when i was moving a window, it turned how it should be with pulse glass, but only that cursor was working.

why is this so hard?

---

### Post by vasa1 on 2012-09-14
> **gandalf3 said:**
> I tried just replacing the "arrow" X11 file in "DMZ-White" to see if it would work. ...why is this so hard?
See if this post helps: [http://ubuntuforums.org/showpost.php?p=11929215&postcount=17](http://ubuntuforums.org/showpost.php?p=11929215&postcount=17)

---

### Post by vasa1 on 2012-09-14
And not to start an argument, but the OP links to what Wikipedia describes as a "[content farm]("http://en.wikipedia.org/wiki/Content_farm")". IMO, it's better to get information from primary sites if possible.

---

### Post by gandalf3 on 2012-09-15
> **vasa1 said:**
> See if this post helps: [http://ubuntuforums.org/showpost.php?p=11929215&postcount=17](http://ubuntuforums.org/showpost.php?p=11929215&postcount=17)

Thanks, now it's kind of reversed.. when in an application it becomes the proper cursor, but on the desktop it's this little black thing... (and a few other thing like the software centre, but when i click/drag something there, it goes to the appropriate pulse-glass cursor) 

maybe if i can find the source file of "the little black thing" i could change that too?
and why is the desktop somehow using a different cursor anyway?
it also reverts temporarily to DMZ-White when resizing windows.

---

### Post by StardustLuna on 2012-10-24
I'm having a similar problem where I've put the cursors that I downloaded in the ~/.icons folder, but they don't show up in the tweak tool to choose from. 

This is the cursor that I want [Gaia Cursor]("http://www.gaia10.us/gallery/gallery-cursors/")

~Stardust

---

