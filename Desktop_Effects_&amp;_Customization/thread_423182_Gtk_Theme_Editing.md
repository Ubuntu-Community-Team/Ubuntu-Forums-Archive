---
title: "Gtk Theme Editing"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by Cervantez on 2007-04-25
If a GTK theme has custom menu-bar backgrounds and the menubar font is changed to white, Apps such as FireFox, ThunderBird, and OpenOffice still have the black font, and it's often unreadable.There is a fix for FireFox and ThunderBird, but none yet for OpenOffice.

I've been trying to get the "LiNsta" GTK theme to look good with readable fonts in openoffice, so I changed the menu-bar background to a whiter colour (which also changed the menubar font to black) ... but the menu bar in the panel is themed aswell (the same background as every other menubar) and it's font is still white, so then I can't read that!

Is there a way to theme every menubar EXCEPT the one in the panel? Or does anyone know how to make the menu-bar font white in OpenOffice? or **is there a way to change the menu-bar (in the panel) font colour to black?**... or any suggestion that may be helpful.

That was probably hard to understand, but a lot of other people are having trouble with it on GnomeLook. Thanks for any help.

---

### Post by leibowitz on 2007-04-25
Yep it's an huge problem. Many themes don't work well with firefox and oo. But I can't give you a solution. You may check on some theme code.

As for the panel, same idea. I know there's Aurora Gtk Engine who does theme the panel, so it must be possible.
[http://www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438](http://www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438)

---

### Post by itsjustarumour on 2007-05-06
> **Cervantez said:**
> If a GTK theme has custom menu-bar backgrounds and the menubar font is changed to white, Apps such as FireFox, ThunderBird, and OpenOffice still have the black font, and it's often unreadable.There is a fix for FireFox and ThunderBird, but none yet for OpenOffice.

I've been trying to get the "LiNsta" GTK theme to look good with readable fonts in openoffice, so I changed the menu-bar background to a whiter colour (which also changed the menubar font to black) ... but the menu bar in the panel is themed aswell (the same background as every other menubar) and it's font is still white, so then I can't read that!

Is there a way to theme every menubar EXCEPT the one in the panel? Or does anyone know how to make the menu-bar font white in OpenOffice? or **is there a way to change the menu-bar (in the panel) font colour to black?**... or any suggestion that may be helpful.

That was probably hard to understand, but a lot of other people are having trouble with it on GnomeLook. Thanks for any help.

Hi Cervantes,

I'm also looking for a fix for this same issue (with Linsta themes) - I've got the menu fonts changed to white in Firefox and Thunderbird OK, but still can't find a way to do it in OpenOffice apps.  If I find a solution, I'll post up and let you know!  :-)

---

### Post by kpolice on 2007-05-06
Yes it's possible to theme the Panel menubar in a different way and yes you can change the font color to whatever colo you want.

---

### Post by Cervantez on 2007-05-06
........well can you tell me how plz?

---

### Post by kpolice on 2007-05-06
```
style "test"{
    fg[NORMAL] = "#ff0000"
    bg[NORMAL] = "#00ff00"
}
widget_class "*Panel*MenuBar*" style "test"
```

Paste this in your theme but first change the colors :p

---

### Post by itsjustarumour on 2007-05-16
> **kpolice said:**
> ```
style "test"{
    fg[NORMAL] = "#ff0000"
    bg[NORMAL] = "#00ff00"
}
widget_class "*Panel*MenuBar*" style "test"
```

Paste this in your theme but first change the colors :p

kpolice - thanks for that - does that go into the gtkrc file?

---

### Post by kpolice on 2007-05-16
Yes, in your theme's gtkrc

---

### Post by itsjustarumour on 2007-05-17
> **kpolice said:**
> Yes, in your theme's gtkrc

Well, gave that a try, but it didn't seem to work. Hmmm...  ](*,)

Not sure what I'm doing wrong.

---

