---
title: "Need help with XFCE"
date: 2005-06-07
forum: Desktop Environments
---

### Post by Psquared on 2005-06-07
For some reason I have lost my right click menu in Xfce and it won't save my background settings. It keeps defaulting back to the plain brown "Human Theme." I think, somehow, another WM is running instead of xfwm4 but I don't know how to find out or how to change it back to xfwm4.

---

### Post by zAo on 2005-06-07
in and terminal type
```

$ xfdesktop &
```
Save the session/log out. Log back in and it is saved :)

---

### Post by Psquared on 2005-06-07
[QUOTE=zAo]in and terminal type
```

$ xfdesktop &
```
Save the session/log out. Log back in and it is saved :)[/QUOTE]

thanks, but that won't do it. as long as the terminal window is open it works, but as soon as a i close it it reverts back to whatever it is running.

i have the session manager set to save but when I logged out and logged back in it was the same.

i also get an error:

> peyre@PTL-Mobile:~ $ xfdesktop &
[1] 9903
peyre@PTL-Mobile:~ $
(xfdesktop:9903): GLib-CRITICAL **: g_hash_table_insert: assertion `hash_table != NULL' failed


any other ideas??

---

### Post by zAo on 2005-06-07
I cant resolve the error message, but try ALT + F2 and type `xfdesktop`. Hope you session will be saved.

---

### Post by skoal on 2005-06-07
It sounds to me like you may have run another DE like Gnome in between XFCE sessions and your ~/.cache settings may have been fubar'd.

1. To see if xfwm4 is running, type 'ps -e |grep x' and see if it's listed.
2. The easiest sol'n may be just to wipe out your ~/.cache folder (which saves per session information).  'cd && rm -rf .cache' outta do it.
3. The "hash table" error you mention is fairly common actually, and I don't know that's even a fatal error in your case.  I believe it occurs when XFCE is trying to resize your panel for new information but there's not enough room in the widget to do so.  I believe the issue is caused by applications using newer function calls in older installed versions of glib.  You might want to check/update your glib/gtk versions.

Mine: libglib 2.6.3 and libgtk 2.6.4

Even when I run synaptic, I get this "error": (synaptic:3794): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

* but it's not fatal.

\\//_

---

### Post by Psquared on 2005-06-07
Yep - that is exactly what happened. So if I delete the ~/.cache file it will make a new one?

---

### Post by Joeb on 2005-06-07
Is it possible that you started nautilus while in XFCE without the "no-desktop" flag?  If so, it took over your desktop.  To remove it, I believe you can just issue a killall nautilus command from a terminal window, then exit and save your session (otherwise, nautilus will automatically restart when you log back in).

---

### Post by Psquared on 2005-06-07
[QUOTE=skoal]It sounds to me like you may have run another DE like Gnome in between XFCE sessions and your ~/.cache settings may have been fubar'd.

1. To see if xfwm4 is running, type 'ps -e |grep x' and see if it's listed.[/quote]

peyre@PTL-Mobile:~ $ ps -e | grep x
 8431 ?        00:00:00 S20xprint
 8432 ?        00:00:00 S20xprint
 8435 ?        00:00:00 S20xprint
10101 ?        00:00:00 xscreensaver
10104 ?        00:00:00 xfce4-session
10107 ?        00:00:00 xfce-mcs-manage
10112 ?        00:00:00 xfwm4
10114 ?        00:00:00 xftaskbar4
10116 ?        00:00:01 xfce4-panel
10229 ?        00:00:12 firefox-bin

> 
2. The easiest sol'n may be just to wipe out your ~/.cache folder (which saves per session information).  'cd && rm -rf .cache' outta do it.

It looks like xfwm4 is running. Should I still do this?

> 
3. The "hash table" error you mention is fairly common actually, and I don't know that's even a fatal error in your case.  I believe it occurs when XFCE is trying to resize your panel for new information but there's not enough room in the widget to do so.  I believe the issue is caused by applications using newer function calls in older installed versions of glib.  You might want to check/update your glib/gtk versions.

Mine: libglib 2.6.3 and libgtk 2.6.4

Even when I run synaptic, I get this "error": (synaptic:3794): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

* but it's not fatal.

\\//_

I have the same version of libglib and libgtk as you.

---

### Post by Psquared on 2005-06-07
[QUOTE=Joeb]Is it possible that you started nautilus while in XFCE without the "no-desktop" flag?  If so, it took over your desktop.  To remove it, I believe you can just issue a killall nautilus command from a terminal window, then exit and save your session (otherwise, nautilus will automatically restart when you log back in).[/QUOTE]

I did do that (start Nautilus in Xfce) , and I've tried the _killall nautilus_ command, but it still won't work.

---

### Post by skoal on 2005-06-07
[QUOTE=Psquared]It looks like xfwm4 is running. Should I still do this?[/QUOTE]

Yeah, you can safely remove the ~/.cache folder.

Just in case, I would back it up first for shizzles and grins.  Something like:

cd && cp -a .cache .cache~

Then:

rm -rf .cache

followed by logging out then back in.  A few things might be different, but nothing dramatic.

\\//_

---

### Post by Psquared on 2005-06-07
[QUOTE=skoal]Yeah, you can safely remove the ~/.cache folder.

Just in case, I would back it up first for shizzles and grins.  Something like:

cd && cp -a .cache .cache~

Then:

rm -rf .cache

followed by logging out then back in.  A few things might be different, but nothing dramatic.

\\//_[/QUOTE]

Funny --- none of these suggestions worked by themselves, but by trying them in combination I was able to get Xfce to save the desktop. I still had no menu (right click) until I ran xfdesktop again. Then I ran the grep command and noticed that the desktop showed up for the first time. I right clicked and I had a partial menu.

I logged out and back in and both the desktop and the partial menu were there. Then I remembered that Xfce has a menu editor that I had fiddled with. I went in and unchecked everything and and saved it and there was my menu!!!!

I remember now I was trying to get rid of the "Debian" menu in the Xfce menu and changed some settings. Now all is back to normal except for that dumb "Debian" entry.

Anyway -- thanks for all the help.

---

### Post by skoal on 2005-06-07
I believe the "Debian" menu comes from the "menu" package.

sudo apt-get remove menu 

should do it.

\\//_

---

### Post by Joeb on 2005-06-07
[QUOTE=Psquared]I did do that (start Nautilus in Xfce) , and I've tried the _killall nautilus_ command, but it still won't work.[/QUOTE]


After killing nautilus, you then have to start up xfdesktop and then exit and save settings.

---

### Post by Psquared on 2005-06-07
[QUOTE=Joeb]After killing nautilus, you then have to start up xfdesktop and then exit and save settings.[/QUOTE]

Thanks. "nothing to kill."

I got it fixed though. Some combination of the suggestions from above (all of which I tried :D ) did it. I really like Xfce as well as Gnome, but its a little faster than Gnome. I just don't like all those extraneous menu entries. For that I like Fluxbox better because it is easy to edit the menu.

I would use Fluxbox all the time, but I have not quite figured out how to configure it with wallpaper and icons yet. Gnome is still good -- just bloated. Window Maker is nice but the dockapps take up too much room. I can't stand KDE because it is too much like M$. (Yes, I have tried 3.4.2 )  \\:D/

---

### Post by jonrkc on 2005-06-07
[QUOTE=Psquared]

I would use Fluxbox all the time, but I have not quite figured out how to configure it with wallpaper and icons yet. [/QUOTE]
I think there's a Fluxbox add-on for backgrounds.  I use chbg for my backgrounds--works with every window manager I've tried, is easy to configure, has tons of special effects if you like that kind of thing, can rotate wallpapers at intervals you set, randomly or otherwise, etc.  If you use it to just set one background, it does that and exits.  

As for icons, I have never liked them, so I don't use them in Fluxbox or in my usual window-manager, IceWM.  But there is a means available for using icons in Fluxbox, and a visit to the Fluxbox home page or else a Google search for "Fluxbox icons" should turn it up.

On my machine, Xfce (which I also use sometimes...) is about ten times as fast as the Gnome environment, which takes forever to load and then to do anything after it's loaded!

IceWM loads in about three seconds (no kidding) and does everything I want, so I keep returning to it.  But I do like the looks of Fluxbox and Blackbox, upon which it's based.

---

### Post by Psquared on 2005-06-07
[QUOTE=skoal]I believe the "Debian" menu comes from the "menu" package.

sudo apt-get remove menu 

should do it.

\\//_[/QUOTE]

Yeah --- I remember now. However, when I try to uninstall it Fluxbox also tries to uninstall. I guess I'll have to put up with it. :-?

---

### Post by jonrkc on 2005-06-07
[QUOTE=Psquared]Yeah --- I remember now. However, when I try to uninstall it Fluxbox also tries to uninstall. I guess I'll have to put up with it. :-?[/QUOTE]
I opened up a Fluxbox session to see about the menu; on mine, there's no "Debian" section.  There is under IceWM and I think under Xfce, though.  

Anyway: I'm pretty sure you can get rid of it by making your own menu out of the automatically generated one in Fluxbox.  Go look at ~/.fluxbox/menu and see the instructions at the top of it.  It tells how to copy it to another location and then edit that menu and change the path for Fluxbox's menu, after which your own menu will be used.  When you edit it as instructed, you can just carefully snip out the "Debian" section.  Formatting is absolutely crucial in these menus, as you probably know, so watch out for removing the wrong curly brace or inserting a blank line that doesn't belong, etc.  But you won't be hurting anything even if you don't succeed the first time, because you can always go back to the automatic Fluxbox menu.

I would have tried it myself, only as I say I don't have the Debian section in mine.

---

### Post by Psquared on 2005-06-08
No Debian menu in Fluxbox -- just in Xfce. If I try to uninstall the "menu" program it tries to uninstall Fluxbox. Don't know of a workaround for this so I'll just leave it.

---

