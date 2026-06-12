---
title: "Gnome panel not transparent"
date: 2010-10-26
forum: Desktop Environments
---

### Post by Eurux on 2010-10-26
Hey guys I have a problem, I want to use an image as my Gnome-panel background but this is what I get: 
[IMG]http://i53.tinypic.com/120qws4.png[/IMG]

This is the image I used as background:
[IMG]http://i51.tinypic.com/x0xq2p.png[/IMG]

Need help :(

---

### Post by gbestrada on 2010-10-26
Did you right clicked on panel ->properties->background -> background image 
,And then selected the image you wanted as background.

---

### Post by stinkeye on 2010-10-26
Because most files outside your home directory are not owned by you,they need to be edited as root.
Press ALT + F2 and enter:

For Ambiance:
```
gksu gedit /usr/share/themes/Ambiance/gtk-2.0/apps/gnome-panel.rc
```

For Radiance:
```
gksu gedit /usr/share/themes/Radiance/gtk-2.0/apps/gnome-panel.rc
```

For both Ambiance and Radiance: comment line 10 which looks like this: "bg_pixmap[NORMAL] = "img/panel.png"". To comment means to add a "#" sign in front of the line (without the quotes). After editing the file, the line should look like this:
# bg_pixmap[NORMAL] = "img/panel.png"

And save the file.


Then change the theme to something else and then switch back to Ambiance or Radiance.

*Some themes don't have a panel.rc file in which case look for and edit
the same line or similar in the themes **gtkrc** file.
Depending on how you installed extra themes, you may also find your theme in
**~/.themes**.(hidden folder in your home directory).

You can also use gnome-color-chooser to change the color of text in the 
panel if that's necessary after making your panel transparent.

---

### Post by bawkqsz on 2010-11-14
Hello, I've been wondering about this, too, tried several different things, including what was mentioned here, with both the gtkrc and panel.rc files, but I have not been able to achieve what I am looking for, which is specifically transparency on the clock and window list. I can get the actual panel transparent, but not the applets . . . is there a way to do that with extra themes?

The theme I'm using is SlicknesS-Black, and the files are thusly:

---

### Post by stinkeye on 2010-11-14
I just had a look at SlicknesS-Black and if I comment out this on line 6 in the gtkrc the applets are transparent.
```
include "panel.rc"
```

---

### Post by bawkqsz on 2010-11-14
Oh wow, that worked perfectly. Thank you!

---

### Post by stinkeye on 2010-11-14
> **bawkqsz said:**
> Oh wow, that worked perfectly. Thank you!
Good to hear.
:)

---

