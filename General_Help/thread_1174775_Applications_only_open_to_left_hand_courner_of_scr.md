---
title: "Applications only open to left hand courner of screen."
date: 2009-05-31
forum: General Help
---

### Post by Jfrench on 2009-05-31
When ever I open (any) application, it will always open in the top left hand corner of my screen. So every time I open an program, I have to move it to where I'm happy with it, before I start using the program.

This isn't by any means a big issue, I use my computer fine every day. Does anyone know a way to get Ubuntu to remember where a program closes, so that it opens up again in the same location.

Thank you for your time in advance!

---

### Post by ActiveFrost on 2009-05-31
As far as I know ( wasn't able to find a solution ), you can't change these things !

---

### Post by jonathanysp on 2009-05-31
Yea i also noticed this on my computer but it doesnt really bother me much. This happens so ubuntu can tile the windows across...if you open a few apps they will appear from left to right so they wont overlap. What app are you using that you need to move it to the correct place? Pdigin? i like my pidgin on the right but for some reason ubuntu remembers that position for me. Maybe you can do something in compiz.

---

### Post by Jfrench on 2009-05-31
I have looked through settings in the compiz settings manager, but there is nothing I can see that will fix the issue (doesn't mean there isn't a setting in there, I just can't find it).

All programs open in the top left hand corner, Firefox, chromium, pidgin, vlc and files, folders and documents I open.

---

### Post by unutbu on 2009-05-31
jfrench, some applications have a way for you to set their "geometry". But it depends on the program. 

Otherwise, it is up to the window manager to decide where to place each window.
If you search the repositories or Ubuntuforums for threads about window managers, you might be able to find one more to your liking.

Or, if you like your current window manager, and just wish you could control window placement better, you could install the devilspie package (See [https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)). (This is what I do.)

Devilspie lets you write little configuration files like this:

```

( if 
  ( and ( is ( application_name ) "Firefox" )
    	( is ( window_name ) "Mozilla Firefox" ))
  ( begin 
    ( geometry "831x1012+842+32" )
  )
)

```

which tells devilspie where to position Firefox windows. You then click System>Pref>Sessions and add /usr/bin/devilspie to the list of programs to run at startup.

---

### Post by HermanAB on 2009-05-31
With KDE you can tell the launcher where to open an application.

One positioning method is with wmctrl:
wmctrl -r <Window Name> -e 0,xpos,ypos,-1,-1

You may also be able to figure out how to specify the position in the .Xdefaults file.

---

### Post by Jfrench on 2009-06-01
For some reason I think that Ubuntu/gnome has remembered my preferred window locations for at least some of my programs in previous versions. I might have to load 8.10 or 8.04 to find out.

---

### Post by jonathanysp on 2009-06-01
i just found out that you can choose where windows appear with the compiz plugin 'place windows' you can specify which program and where they appear.

---

