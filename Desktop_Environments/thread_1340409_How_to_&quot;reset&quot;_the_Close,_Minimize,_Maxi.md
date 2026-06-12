---
title: "How to &quot;reset&quot; the Close, Minimize, Maximize buttons?"
date: 2009-11-28
forum: Desktop Environments
---

### Post by CBR1100XX on 2009-11-28
Ok, I've been toying around with Ubuntu making it look like OS X (again) and got it working and looking the way I wanted.  But the "Oooh" effect has now worn off, and I wanted something more subtle on the eyes.

I changed the theme back to a default theme, but the minimize/maximize/close buttons are on the left side (like mac) and I'd love to get them back to their default position on the right side.

I'm no wizard when it comes to this stuff, so keep that in mind. ;)

[IMG]http://img442.imageshack.us/img442/6531/screenshotfh.png[/IMG]

---

### Post by prshah on 2009-11-28
> **CBR1100XX said:**
> the minimize/maximize/close buttons are on the left side 
get them back to their default position on the right side.


Open gconf-editor by pressing Alt+F2, and giving the command ```
gconf-editor
```; then browse to /apps/metacity/general/button_layout
, and change the layout order. The button preceding the ":" will appear in the left corner of the title, and the buttons succeeding the ":" will appear in the right edge.

As an example, I use```
menu:minimize,maximize,spacer,close
```

---

### Post by CBR1100XX on 2009-11-28
Thank you PRS, appreciate the help!

---

### Post by DomesDKG on 2010-04-30
Thank you, brilliant solution!

---

### Post by alvevind on 2010-04-30
The cleanest way to restore the window button position is to install the right aligned theme:

Step-by-step procedure:
1. Download the modified theme [http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz](http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz)
2. Open the menu "System" > "Preferences" > "Appearance"
3. Click the button "Install"
4. Open the folder "Downloads"
5. Select the file "Ambience_Radiance-Right.tar.gz"
6. Click "Open"
7. Select the new theme "Ambiance-right"

You then have both the standard unmodified left-aligned theme and the right-aligned theme available and can easily switch back and forth between them with a single click.

---

### Post by browolf on 2010-04-30
> **prshah said:**
> Open gconf-editor by pressing Alt+F2, 

...

As an example, I use```
menu:minimize,maximize,spacer,close
```

my buttons mysteriously moved last night when I upgraded to lucid. Talk about disconcerting! 

this solution: instant fix.

---

### Post by ricardisimo on 2010-04-30
> **prshah said:**
> Open gconf-editor by pressing Alt+F2, and giving the command ```
gconf-editor
```; then browse to /apps/metacity/general/button_layout
, and change the layout order. The button preceding the ":" will appear in the left corner of the title, and the buttons succeeding the ":" will appear in the right edge.

As an example, I use```
menu:minimize,maximize,spacer,close
```

I'm hoping that editing metacity will be a bit more intuitive in the future. There's no reason anyone would know how to edit that line in gconf-editor to get those results. "Window buttons on upper/lower right/left" should probably be part of System >> Preferences >> Appearance instead.

The obsession with Mac at GNOME is out of control. Whatever happened to "sane defaults"? How does changing what no one is complaining about constitute "sane"? I would think "leave it alone" would be sane.

---

### Post by prshah on 2010-05-01
> **ricardisimo said:**
> I'm hoping that editing metacity will be a bit more intuitive in the future.

Oh it gets worse; actually, on most systems, the Desktop Manager is compiz and not metacity. Metacity does not even run unless compiz cannot be launched (which is getting rarer and rarer these days). Luckily, compiz reads metacity's preferences. 

I don't have the slightest idea how to reverse this if only Compiz's settings were involved.

---

