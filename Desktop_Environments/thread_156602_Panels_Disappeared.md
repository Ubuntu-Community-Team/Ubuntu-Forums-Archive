---
title: "Panels Disappeared"
date: 2006-04-07
forum: Desktop Environments
---

### Post by Tom B on 2006-04-07
So I booted my computer up this morning, logged in, and found that both the top and the bottom panels were gone.  My desktop background is still there, but the panels aren't. When I do open a window and minimize it, it goes to nowhere. I have read a number of people with similar problems, but the solution is always "right click on the panel and add the window list." My problem is that I don't have a panel to right click on. Any idea what happened or how to fix it?

---

### Post by mgmiller on 2006-04-07
Are you sure your panels haven't been slid off the right or left side of the screen?  Is there a small verticle bar on the top or bottom at the extreme right or left side?  If not, are you sure you are seeing your entire desktop?  You may need to adjust the settings on your monitor to be sure you are seeing the whole width of the dektop.  If the bar is there, just click it and the panel will slide back into view.  Is it possible you made the panels transparent?  try right clicking where the panels should  be and see if there are any panel options available.  Another option is to boot off a 5.10 install CD and select the option to fix your install.

Good luck

---

### Post by aysiu on 2006-04-07
Press Alt-F2 and type ```
gnome-panel
```

---

### Post by Tom B on 2006-04-07
The panels weren't slid off, and they aren't transparent, I just get the desktop menu when I right click at the top or bottom. I changed the monitor settings around- I'm definitely seeing the whole screen. I can see the part of the background that used to be hidden behind the panels. I did find this in a FAQ.

"The panel disappeared! What do I do?

My desktop started up one day with no panels at all (i.e. no "applications, computer" menu at the top, and no task list at the bottom). I don't know why.

The fix was to start a terminal (right click on desktop, "open terminal") and run the command "gnome-panel". They started up again fine ... I checked "Computer|Desktop Preferences|Sessions|Current Session" and scrolled down to confirm that "gnome-panel" has the Style "restart" ... so I stopped the command-line panels (by hitting ctrl-C in the terminal) and the panels vanished, and restarted happily."

But when I right click on the desktop, there isn't an "open terminal" option. I assume Alt-F2 is supposed to be a shortcut to open the terminal, but nothing happens when i press it. I booted my install cd, but didn't see an option to fix my install. Did I miss something?

Thanks for the quick answers.

---

### Post by aysiu on 2006-04-07
Alt-F2 is the shortcut for the Run dialogue, not the terminal.

If Alt-F2 isn't working, something's seriously wrong--more than just your panel being missing.

---

### Post by Tom B on 2006-04-07
Well, that's not good. Is there a default keyboard shortcut for opening the terminal? I've searched, but all I can find is keyboard shortcuts for when you are in the terminal. It's odd, plenty of other shortcuts work- log out, restart, lock screen, minimize/maximize, and alt-tab are all working fine. But not Alt-F2.

---

### Post by aysiu on 2006-04-07
No. There's no default keyboard shortcut for the terminal.
You can define one, but there's no default.

I'm not sure if this'll work, but you can try this:

Press Control-Alt-F1
Log in
Type ```
gnome-panel
``` Press Control-Alt-F7

I doubt it'll work, but it's worth a try...

---

### Post by Tom B on 2006-04-08
No luck. "-bash: gnome-panel: command not found"  I was looking around the forum, and someone had a similar problem and a suggested solution was  "you could also try moving your /home/username/.gnome2/panel2.d folder to /home/username/.gnome2/backup_panel2.d and restarting gnome..." Well, that didn't work, but all my launchers that were on the panel are in that folder, and when I open them they open the program just as if they were on the panel. So now at least I can use most of the programs I normally do anyway (open office, rythymbox, firefox, etc.) Kind of annoying that I don't have any of the other things from the menus and I can't minimize anything, but at least it's semi-functional. Next time, I'll define a keyboard shortcut for terminal. Thanks for all your suggestions.

---

### Post by aysiu on 2006-04-08
Maybe you can try ```
sudo apt-get update
sudo apt-get install --reinstall gnome-panel
```

---

### Post by ec2 on 2006-04-08
don't worry, u can always use alt+tab to change windows, and if you can't then ur scrued...

---

### Post by Ubuntuud on 2006-04-08
Maybe you should install XFCE or KDE so you can fix your problem more easily, it quite hard to do everything with shortcuts. (sudo apt-get install kde/sudo apt-get install xfce4)

---

### Post by Tom B on 2006-04-08
That worked wonderfully, aysiu. After a GNOME restart, my panels are back with my launchers and everything. Thanks a lot. Still a minor problem, though. When I restarted, a little window popped up saying "The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet". Do you want to delete the applet from your configuration?" Then it gave me the options "delete" "don't delete." Same thing with the volume control. I chose "delete" because I thought I could just right click and add them right back to the panel. But I don't see either of them in the "Add to Panel" menu. It's no big deal because my volume keyboad shortcuts still work, and the trash is easy enough to get to without a launcher, but if there is an easy fix or I'm missing something obvious it would be nice to have them back. Thanks again.:-D

---

### Post by aysiu on 2006-04-08
Wouldn't it make sense that you could try reinstalling gnome-panel yet again and then choose not to delete...?

---

### Post by oliverlewis on 2007-11-23
[SIZE="3"]Hi, I've been following your posts and have a similar problem. I do see the panel flash up on the desktop when first logging in, but then it disappears. I tried gnome-panel in a terminal and I got this/these errors:[/SIZE]

[COLOR="Gray"](gnome-panel:10805): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GtkImageMenuItem' has no property named `has-tooltip'

(gnome-panel:10805): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1669: signal `query-tooltip' is invalid for instance `0x729ee0'

(gnome-panel:10805): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GtkImageMenuItem' has no property named `has-tooltip'

(gnome-panel:10805): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1669: signal `query-tooltip' is invalid for instance `0x97a0d0'

(gnome-panel:10805): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GtkImageMenuItem' has no property named `has-tooltip'

(gnome-panel:10805): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1669: signal `query-tooltip' is invalid for instance `0x97a230'

(gnome-panel:10805): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GtkImageMenuItem' has no property named `has-tooltip'

(gnome-panel:10805): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1669: signal `query-tooltip' is invalid for instance `0x97a390'

(gnome-panel:10805): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GtkImageMenuItem' has no property named `has-tooltip'

(gnome-panel:10805): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1669: signal `query-tooltip' is invalid for instance `0x97a4f0'

(gnome-panel:10805): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GtkImageMenuItem' has no property named `has-tooltip'

(gnome-panel:10805): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1669: signal `query-tooltip' is invalid for instance `0x97a650'

(gnome-panel:10805): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GtkImageMenuItem' has no property named `has-tooltip'

(gnome-panel:10805): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1669: signal `query-tooltip' is invalid for instance `0x98a800'

(gnome-panel:10805): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GtkImageMenuItem' has no property named `has-tooltip'

(gnome-panel:10805): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1669: signal `query-tooltip' is invalid for instance `0x98aac0'

(gnome-panel:10805): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GtkImageMenuItem' has no property named `has-tooltip'

(gnome-panel:10805): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1669: signal `query-tooltip' is invalid for instance `0x729d80'

(gnome-panel:10805): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `PanelPlaceMenuItem' has no property named `has-tooltip'

(gnome-panel:10805): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1669: signal `query-tooltip' is invalid for instance `0x777ae0'

(gnome-panel:10805): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `PanelDesktopMenuItem' has no property named `has-tooltip'

(gnome-panel:10805): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1669: signal `query-tooltip' is invalid for instance `0x69e920'

(gnome-panel:10805): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `ButtonWidget' has no property named `has-tooltip'

(gnome-panel:10805): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1669: signal `query-tooltip' is invalid for instance `0x777cc0'
gnome-panel: symbol lookup error: /usr/lib/gnome-panel/libwnck-applet.so: undefined symbol: gtk_widget_set_tooltip_text
[/COLOR]
[SIZE="3"]Then I did a reinstall of gnome-panel as was suggested. [/SIZE]

 [COLOR="Gray"]sudo apt-get install --reinstall gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavcodec0d libavformat0d emerald libemeraldengine0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B/504kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 163081 files and directories currently installed.)
Preparing to replace gnome-panel 1:2.20.1-0ubuntu1 (using .../gnome-panel_1%3a2.20.1-0ubuntu1_amd64.deb) ...
Unpacking replacement gnome-panel ...
Setting up gnome-panel (1:2.20.1-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
[/COLOR]

[SIZE="3"]I can see it flash up on the screen for a split second. Now I get this error:[/SIZE]

[COLOR="Gray"]gnome-panel: symbol lookup error: /usr/lib/gnome-panel/libwnck-applet.so: undefined symbol: gtk_widget_set_tooltip_text
[/COLOR]
[SIZE="3"]
I hope this is fixing the problem. Should I also try to reinstall it again? Any help is much appreciated,
Oliver[/SIZE]

---

### Post by xfile087 on 2007-11-23
I had the same problem so I deleted ~.config/autostart and it started working for a while. It then stopped working again! So I disabled compiz fusion and now I don't have one single problem! I think it's something to do with compiz because if while the panels are disabled I enabled or disable a compiz effect (such as Negative), the panels suddenly show up again...

---

### Post by oliverlewis on 2007-11-25
Thanks[SIZE="3"] xfile087[/SIZE] for your reply.
Is the ~.config/autostart located in my home folder?
And where should l look for commandline to disable compiz?
Also, does the fact that Alt+F2 is not working have something to do with it?
Thanks again and in advance,
-Oliver

---

### Post by oliverlewis on 2007-11-25
I found how to disable Compiz.
[http://ubuntuforums.org/showthread.php?t=574092]("http://ubuntuforums.org/showthread.php?t=574092")
But that didn't seem to work.  I also uninstalled compiz. I am going to try to restart X.

---

### Post by oliverlewis on 2007-11-25
[SIZE="2"]I tried  an upgrade for apt-get and got the gnome system tools  upgrade will this fix my Alt+F2 problem?[/SIZE]

root@ubuntu:/home# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gnome-system-tools
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3097kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main gnome-system-tools 2.20.0-0ubuntu2 [3097kB]
Fetched 3097kB in 10s (297kB/s)                                                
(Reading database ... 163103 files and directories currently installed.)
Preparing to replace gnome-system-tools 2.20.0-0ubuntu1 (using .../gnome-system-tools_2.20.0-0ubuntu2_amd64.deb) ...
Unpacking replacement gnome-system-tools ...
Setting up gnome-system-tools (2.20.0-0ubuntu2) ...

---

### Post by oliverlewis on 2007-11-25
Ok I just did a synaptic uninstall of compiz and got this in the terminal I ran it from:

[COLOR="SlateGray"](yelp:5951): Yelp-WARNING **: Cannot find dbus bus


(yelp:5951): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(yelp:5951): atk-bridge-WARNING **: IOR not set.

(yelp:5951): atk-bridge-WARNING **: Could not locate registry

(yelp:5951): Yelp-WARNING **: beagled not running, using basic search support.

(yelp:5951): Yelp-WARNING **: beagled not running, using basic search support.

(yelp:5951): Yelp-WARNING **: beagled not running, using basic search support.[/COLOR]

I am not sure if this is something to be concerned about or if I am beating a dead horse but, I would really like to keep using this installation of Ubuntu.

---

### Post by xfile087 on 2007-12-04
> **oliverlewis said:**
> Thanks[SIZE="3"] xfile087[/SIZE] for your reply.
Is the ~.config/autostart located in my home folder?
And where should l look for commandline to disable compiz?
Also, does the fact that Alt+F2 is not working have something to do with it?
Thanks again and in advance,
-Oliver

~ = home folder. So yep, the folder your looking for is in your home folder. - /home/myusername/.config/autostart

I'm not sure about the Alt+F2 problem as I can't say I've really had any problems with that.

I hope you manage to get it sorted!

---

