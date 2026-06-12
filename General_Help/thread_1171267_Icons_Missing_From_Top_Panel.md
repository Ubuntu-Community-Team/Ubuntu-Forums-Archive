---
title: "Icons Missing From Top Panel"
date: 2009-05-27
forum: General Help
---

### Post by loweehahn on 2009-05-27
Today when I boot up my laptop I was shocked to see that all my icons except for the volume icon disappeared in the top panel. The interent connection icon, bluetooth icon, amsn icon and so on all gone! How can I restore them back?

---

### Post by x33a on 2009-05-27
first confirm that those programs are running.

and what did you last do, which you think might have caused the problem.

---

### Post by loweehahn on 2009-05-27
Yeah the programs were running. I'm just shocked la that this happened suddenly. I searched about this problem in the internet and one website said it's a bug.

---

### Post by x33a on 2009-05-27
did you try a restart or log off / on.

and are those still enabled in the startup.

---

### Post by loweehahn on 2009-05-27
I only tried logging off. Yeah they still function and are still there at the startup. Just that it's no longer at the notification area. Bluetooth function can't be used since the icon is not there.

---

### Post by x33a on 2009-05-27
well, if it's a bug, then you'll have to wait for a fix :)

---

### Post by drs305 on 2009-05-27
If you are using ubuntu, in the future you can try to refresh them by running:
```
killall gnome-panel
```
That will redraw the desktop and may restore your panels.

If not, and you didn't have a great deal of customization, you can restore the default panels with:
```

gconftool-2 --recursive-unset /apps/panel
killall gnome-panel

```

You *should* be able to right click the panel, Add to Panel, Notification Area to get that back.

---

### Post by CatKiller on 2009-05-27
> **loweehahn said:**
> Today when I boot up my laptop I was shocked to see that all my icons except for the volume icon disappeared in the top panel. The interent connection icon, bluetooth icon, amsn icon and so on all gone! How can I restore them back?

Do you mean all of them, or just the ones in the Notification Area?

Right-click on panel -> Add to Panel... -> Notification Area.

---

### Post by loweehahn on 2009-05-28
Only the notification icons. But now ok already after following drs305's instructions.

---

### Post by drs305 on 2009-05-28
Glad you got the panel restored. Just a tip: If you do a lot of panel modifications you might want to back them up from time to time. As you saw, you could just copy the panel folder, where they are retained, but you can also use the terminal (and make a shortcut) to save and restore your panel settings:

To save:
```
gconftool-2 --dump /apps/panel > **~/Desktop/panels**
```
To restore:
```
gconftool-2 --load **~/Desktop/panels** && killall gnome-panel
```
This saves the panel settings to a file on your Desktop called *panels* but you can place it wherever you wish. The [I]killall/I] command will refresh the panels, despite the ominous sound of it.

---

### Post by loweehahn on 2009-05-28
Where do you learn all these command lines? Where can I learn all the commands?

---

### Post by drs305 on 2009-05-28
> **loweehahn said:**
> Where do you learn all these command lines? Where can I learn all the commands?

I learn a lot from these forums and the *man* pages. 

If you are interested in a command, you type "man <command-name>" in a terminal. Example: man cp   The switches available to the commands is where the power of the commands really become apparent.

I really like gconf-editor, which was related to this thread. It contains many of the user settings. You can open it with "gconf-editor" or via System Tools, Configuration Editor, if you have it enabled in the menu. Many of the most used settings are stored in "apps/nautilus" and "apps/metacity" folders. 

Things such as whether to show the Desktop, volumes/partitions, automounting, icon size, etc are listed. The settings can be made in other ways but gconf-editor is like a central repository.

As to learning *all* the commands, there are more than I could ever possibly get to. I pick them up as I use them, which has two advantages. Not as many to concentrate on, and they are the ones I will actually *use*.  ;-)

[http://www.linuxcommand.org/superman_pages.php]("http://www.linuxcommand.org/superman_pages.php")

---

### Post by christianshearer on 2009-06-05
I lost my icon that shows me my current internet connection status (the two computers or the four bars for wifi).  It is not in the "add to panel" selection, and when I tried to refresh my panel like was explained earlier in this thread it did not work.  I'm using Ubuntu 9.04

Any help with this one?  

(I'm fairly illiterate, but can copy and paste to the terminal like a champ)

thanks

---

### Post by loweehahn on 2009-06-05
Very sorry to hear this christanshearer. I haven't encounter such problem and luckily my problem was resolved. Sounds horrible. Hopefully someone will be able to help you. :)

---

### Post by CatKiller on 2009-06-05
Right-click on Panel -> Add to Panel... -> Notification Area.

---

### Post by J A Smith on 2009-06-05
Sorry to hijack this thread, similar problem. My notification area is gone, tried the above solutions to no avail. When I click on 'add notification area', nothing happens. Any ideas?

Thanks!

---

### Post by loweehahn on 2009-11-29
Another problem has occurred. Today when I switch on my computer suddenly I notice my icons are not in order. For example the trash icon is now in the middle of the panel and same goes to the weather, date and time icon. How can I restore them back to original?

---

### Post by raktarok on 2009-11-29
Have you tried the 'lock to panel' feature? Its on the right click menu of every applet.

---

### Post by loweehahn on 2009-11-30
Whether I untick or tick it I still can't move the icons.

---

### Post by loweehahn on 2009-11-30
Ok I got it already. My icon panels are now in order. Thanks a lot. :)

---

