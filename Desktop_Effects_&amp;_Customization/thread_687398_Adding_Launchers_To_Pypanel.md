---
title: "Adding Launchers To Pypanel"
date: 2008-02-04
forum: Desktop Effects &amp; Customization
---

### Post by Mark76 on 2008-02-04
I want some quick launchers on pypanel so I don't have to keep minimising windows to get the right click menu.  I tried editing the pypanel.rc file, but I'm not sure I've done it right

> # Application Icon List: List of custom icons for specific applications
# The application name is its WM_CLASS name, use 'xprop' to find WM_CLASS
#
# The "default" entry is used for applications with no icon.  If left "",
# PyPanel will use the default icon distributed with the source.
#
# Add entries using the following format -
#     "<application name>" : "<full path to icon>",
#------------------------------------------------------------------------------
ICON_LIST       = {
                   "default" : "usr/share/pixmaps",
                   "example" : "/usr/share/imlib2/data/images/audio.png",
                  }
                  
#------------------------------------------------------------------------------
# Application Launch List: Ordered list of icons and applications for the
#                          application launcher.
# 
# Add entries using the following format -
#     ("<executable>", "<full path to icon>")
#------------------------------------------------------------------------------
LAUNCH_LIST     = [
                   ("gimp-2.2", "/usr/share/icons/xquisite/scalable/apps/gimp.png"), 
                  ]


If someone could post an example of what it should look like, I'd be very grateful.

Oh, and a show desktop launcher would be useful as well.

---

### Post by Tenken on 2008-02-04
What entry have you added exactly? That looks like the sample config file.

Anyway,  to add the launcher for xterm add this entry between the launch list brackets []

```
("xterm","/path/to/terminal/icon")
```

And make sure the launcher section is showing under the "Panel Layout" section.

---

### Post by Mark76 on 2008-02-04
This

> ("gimp-2.2", "/usr/share/icons/xquisite/scalable/apps/gimp.png" ),

Did I do it wrong?

---

### Post by Tenken on 2008-02-04
Looking at it again it might just be a typo. Is that a space between "gimp." and "png" at the end of the icon path? Also double check if it is a .png extension, scalable icons are usually .svg.

---

### Post by Mark76 on 2008-02-04
Yes, it is a space :oops:

Which is odd, because there's no space in the line in the file.

And it's definitely a .png

---

### Post by Mark76 on 2008-02-04
I edited the pypanel.rc file and updated the gimp line to reflect the fact that it's a newer version (2.4.2) than the one listed.

Still nothing.

---

### Post by Tenken on 2008-02-04
What command do you to launch the GIMP from terminal? I don't think you need the version number, just ```
("gimp","/usr/share/icons/xquisite/scalable/apps/gimp.png"),
```

---

### Post by Mark76 on 2008-02-04
gimp is the command to open gimp in the terminal. I edited the line to just say "gimp"... but still no icon on the panel.

Will now try it without quotation marks.

---

### Post by Mark76 on 2008-02-04
Have I got the wrong end of the stick with this?

Maybe it's not meant to create panel launchers.

---

### Post by urukrama on 2008-02-04
Make sure you have the lauchers enabled in the following section:

> 
#------------------------------------------------------------------------------
# Panel Layout:       -----------------------------------
#                     [  1  ][  2  ][  3  ][  4  ][  5  ]
#                     -----------------------------------
#
# The panel layout is split into 5 sections numbered 1, 2, 3, 4 or 5 as shown
# in the diagram above.  Each of the following objects can be enabled by
# assigning it a section number or disabled by assigning it 0:
#------------------------------------------------------------------------------
DESKTOP         = 1             # Desktop name section
TASKS           = 2             # Task names section 
TRAY            = 5             # System tray section
CLOCK           = 4             # Clock section
LAUNCHER        = 0             # Application launcher section

#------------------------------------------------------------------------------

Change the numbers to whatever order you want the parts of pypanel to show. 1 is on the left, and 2-5 come after it in that order. If you don't want a part to show, you give it 0 (as above on the launcher line).

---

### Post by Mark76 on 2008-02-04
Okay, I edited that section and changed the Launcher from 0 to 5, then rearranged the [1][2][3][4][5] layout to [5][1][2][3][4], killed pypanel, restarted it and still no icon.

---

### Post by Mark76 on 2008-02-04
Okay, I finally worked out how to get the launchers to show and where but now I get this

> Failed to open ~/.pypanelrc -

invalid syntax (.pypanelrc, line 125)

Line 125 reads

 SHADE = 50

Note, the original has a big space in front of the = sign

---

### Post by Tenken on 2008-02-04
So you got the config file to work with launchers showing, then edited the the shade and now it won't work? I wouldn't think a space would matter that much, but try putting it back in. And if you still can't get it to work could you post your whole .pypanelrc for me to try out on my machine?

---

### Post by Mark76 on 2008-02-05
That's the problem. I didn't edit line 125 at all.

What should it say?

---

### Post by Tenken on 2008-02-05
My config file has different line numbers than your but my shade section looks like this

```
------------------------------------------------------------------------------
# Background Alpha/Shade Level: 0 (Fully Translucent) -> 255 (Fully Opaque)
# BG_COLOR is used for tinting
#------------------------------------------------------------------------------
SHADE           = 127
```

---

### Post by Mark76 on 2008-02-05
I changed the line to 127 and I'm still getting the same error when I run it in the terminal

---

### Post by Tenken on 2008-02-05
The 127 is just the transparency setting, the number shouldn't matter as long as it's between 0 (transparent) and 255 (solid). I just chose 127 because it's the half way point.

---

### Post by Mark76 on 2008-02-05
Then what the hell is wrong with the bleeding syntax?

---

