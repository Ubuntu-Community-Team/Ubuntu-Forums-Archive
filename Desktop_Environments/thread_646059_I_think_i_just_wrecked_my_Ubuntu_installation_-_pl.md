---
title: "I think i just wrecked my Ubuntu installation - please help!!"
date: 2007-12-20
forum: Desktop Environments
---

### Post by lenswipe on 2007-12-20
I recently saw a video on youtube showing a person with cube desktop who had the windows sticking out above the desktop when it rotated. So i thought i would try this myself, so i went into the compiz dialog box and selected the "Widow Widget Layer" effect. It didnt apear to be having any effect so i went in to the settings for it under the behaviour tab in widget windows i went into the empty box that said: Widget Windows and pasted in the following:

```
((type=Normal | Utility | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
```

whcih i obtained from the close animation tab under the Animations button.

When i try and open a window it just shuts again (DUH!!)

can someone tell me if there is a way out of this rut without re-installation.

I am happy to provide any info such as system logs if you tell me where to look for it 



Thanks :D

---

### Post by andrewc6l on 2007-12-20
I don't think you'll have to reinstall. I'm not familiar with what you did, but in general you can hit Ctrl-Alt-F1 (or is it Ctrl-F1?) to get yourself to a TTY login, and from there to a command line. Then you can probably do something like:

find ~ -name \* -print | xargs grep 'name=sun-awt-X11-XFramePeer'

to find the file with your configuration info, and modify it using an editor.

---

### Post by PeterJS on 2007-12-20
Looks like all of your windows are opening to the widget layer. The default key to bring up the widget layer is F9. See if that will get you to where you can see your windows, from there run ccsm and set that back to blank. The plugin you were looking for is called 3d windows and has been ported to Compiz Fusion yet from beryl (which is funny I thought the point was for the beryl plugins to just work, silly me).

---

### Post by linuxunil on 2007-12-20
you can turn off compiz by hitting alt-f2 then entering
```
metacity --replace
```
that will replace compiz with metacity (default gnome manager) as your window manager.

After you get metacity up go in and reset the setting that you changed.

As long as you have your session set up to automatically start compiz, it will start after you log out and back in.

Also the widget window layer is not what you wanted, it is more like dashboard on OS X or Yahoo widgets.

If you give a link to the video some one here might be able to help you figure out how to set them up.

---

