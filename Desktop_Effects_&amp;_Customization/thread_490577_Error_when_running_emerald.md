---
title: "Error when running emerald"
date: 2007-07-02
forum: Desktop Effects &amp; Customization
---

### Post by virgilnilson on 2007-07-02
When I start emerald in terminal, I get this feedback:

```
  emerald --replace &
[1] 8849
virgil@computer:~$ 
(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8849): Wnck-WARNING **: Unhandled action type (nil)


```

otherwise, it seems to be working, but if I close the terminal window, I suddenly lose my window decorations/title bars. If I start it up as compiz --replace -c emerald &, I get this:

```
compiz --replace -c emerald &
[1] 9147
virgil@computer:~$ Adding plugin firepaint (firepaint)
Adding plugin winrules (winrules)
Adding plugin screenshot (screenshot)
Adding plugin glib (glib)
Adding plugin fadedesktop (fadedesktop)
Adding plugin switcher (switcher)
Adding plugin snow (snow)
Adding plugin video (video)
Adding plugin neg (neg)
Adding plugin minimize (minimize)
Adding plugin scale (scale)
Adding plugin splash (splash)
Adding plugin water (water)
Adding plugin vpswitch (vpswitch)
Adding plugin dbus (dbus)
Adding plugin showdesktop (showdesktop)
Adding plugin trailfocus (trailfocus)
Adding plugin imgjpeg (imgjpeg)
Adding plugin fakeargb (fakeargb)
Adding plugin resizeinfo (resizeinfo)
Adding plugin wobbly (wobbly)
Adding plugin move (move)
Adding plugin zoom (zoom)
Adding plugin bench (bench)
Adding plugin resize (resize)
Adding plugin plane (plane)
Adding plugin cube (cube)
Adding plugin svg (svg)
Adding plugin clone (clone)
Adding plugin rotate (rotate)
Adding plugin opacify (opacify)
Adding plugin crashhandler (crashhandler)
Adding plugin ring (ring)
Adding plugin regex (regex)
Adding plugin wall (wall)
Adding plugin png (png)
Adding plugin cubereflex (cubereflex)
Adding plugin scaleaddon (scaleaddon)
Adding plugin fade (fade)
Adding plugin addhelper (addhelper)
Adding plugin decoration (decoration)
Adding plugin expo (expo)
Adding core settings (General Options)
Adding plugin place (place)
Adding plugin text (text)
Adding plugin fs (fs)
Adding plugin animation (animation)
Adding plugin mblur (mblur)
Adding plugin inotify (inotify)
Adding plugin thumbnail (thumbnail)
Adding plugin group (group)
Adding plugin reflex (reflex)
Adding plugin put (put)
Adding plugin tile (tile)
Adding plugin blur (blur)
Adding plugin annotate (annotate)
Adding plugin snap (snap)
Adding plugin extrawm (extrawm)
Backend     : gconf
Integration : true
Profile     : default
Initializing core options...done
Initializing minimize options...done
Initializing water options...done
Initializing move options...done
Initializing zoom options...done
Initializing resize options...done
Initializing ring options...done
Initializing decoration options...done
Initializing place options...done
Initializing animation options...done
Initializing mblur options...done
Initializing thumbnail options...done
Initializing reflex options...done
Initializing snap options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing fade options...done
Initializing cube options...done
Initializing rotate options...done
Initializing cubereflex options...done
Initializing expo options...done
Initializing switcher options...done
Initializing scale options...done
Initializing scaleaddon options...done

```

Once again, everything seems to work, but if I close the terminal, I lose all the same stuff again. I'm not sure if it's related, but I also have to run one of these commands every time I want to try a new emerald theme, as just clicking the theme does nothing.

When running it as a script on startup, there don't seem to be any problems except that the emerald themes won't refresh when I select a new one.

Also, when trying to fetch non-GPL themes, I get multiple errors saying "error calling tar".

---

### Post by dwebb86 on 2007-07-02
That long list of the same error doesn't matter as long as your program runs fine.

Also, you can use ALT+F2 to run those commands instead of the terminal and you won't have that 'when I close the terminal I lose them' problem.

I don't know about not being able to refresh your emerald theme, I suggest using ALT+F2 and entering multiple combinations and orders of the three commands:
compiz --replace
emerald --replace
and compiz --replace -c emerald &

and just figuring out what order/combo works for you.

---

