---
title: "Window and Toolbar Sizes"
date: 2009-01-14
forum: General Help
---

### Post by codfish45 on 2009-01-14
So, I have two problems relating to size of things:

1.  The size of toolbars and tabs (eg Firefox, Nautilus).
        
This took me a bit to realize it bothered me, but the toolbars and such seem to be about 25% too big, not so big that it looks bad, but big enough that it makes the screen seem crowded/cramped.  My screen is set to its max resolution (1024x768), so I don't think that's the issue.  Is there a line I can tweak in my theme's gtkrc file to change their pixel height or something?

2.  The size of certain non-scrollable windows (eg Preferences and setup windows)

Some of the "Preferences" windows are so long that they will not fit on a single desktop, and the only way to hit the "okay" or "apply" or "whatever" button is to disable my desktop cube and use a second row of workspaces just to look at it.  Granted, this is pretty app specific, but I've noticed it in a few places, including common ones like Evolution.
For example, with Cinelerra:
[IMG]/home/jay/Desktop/Screenshot-1.png[/IMG]
[IMG]/home/jay/Desktop/Screenshot-2.png[/IMG]

Anyone know anything about this?
Even with these minor annoyances, I still like the look of things better than my XP desktop, but it would be nice to iron out these last few wrinkles.  Any help would be greatly appreciated.
Thanks!

---

### Post by gettinoriginal on 2009-01-14
Go to appearance, fonts, details, mine is set to 96 by default, and looks normal.  :P

---

### Post by codfish45 on 2009-01-14
Awesome!  That did the trick, mine was up to 98.  86 seemed to do the trick for me.

Edit:  If anyone else is having this problem and using Firefox and/or Thunderbird, you will need to change "layout.css.dpi" to 0 in about:config before it takes effect in either app.

---

### Post by codfish45 on 2009-01-14
Although, still need to get those weird preference windows straightened out.
Any suggestions?

---

### Post by gettinoriginal on 2009-01-15
Don't know if it will work, but try this in terminal:
```
compiz --replace
```

---

### Post by blackened on 2009-01-15
> **codfish45 said:**
> Although, still need to get those weird preference windows straightened out.
Any suggestions?

Much easier than disabling your cube, hold down alt to enable moving of the window by clicking anywhere on it, then dragging it to the appropriate spot that will give you access to the buttons at the bottom.

---

### Post by codfish45 on 2009-01-15
> **blackened said:**
> Much easier than disabling your cube, hold down alt to enable moving of the window by clicking anywhere on it, then dragging it to the appropriate spot that will give you access to the buttons at the bottom.

It still won't let me move the top of the frame past my top panel...

---

### Post by gettinoriginal on 2009-01-15
The next time you have to disable your cube and can get at the bottom of a pref window, try to drag (manually) the bottom of the window up.  Another thing you can try is hitting F11 twice, then manually minimize window, then maximize with the max button. (don't know about that one, just a guess) ;)

---

### Post by blackened on 2009-01-15
> **codfish45 said:**
> It still won't let me move the top of the frame past my top panel...

Sorry, should have remembered that:

```
gconftool-2 --type bool --set /apps/compiz/plugins/move/allscreens/options/constrain_y 0
```

---

### Post by codfish45 on 2009-01-15
The gconfig was the key.  Thanks!

---

