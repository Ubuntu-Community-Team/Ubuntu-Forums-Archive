---
title: "missing menu bar in open apps"
date: 2009-06-23
forum: Desktop Environments
---

### Post by SteveNorman on 2009-06-23
I am using gnome, compiz, emerald, nvidia 188.4 driver, 

When I use my gnome desktop, none of my open apps have the menu bar with file, edit, view etc. They do have a title bar, and the closing and minimising symbols.
When I use fluxbox or KDE the menu bars are in place. 

I cant seem to find anybody with these problems in my searches. Most searches yield results for the panel menus and not the apps menus. 

BTW I suspect its my compiz install, however compiz works fine for everything else, rotating spheres, paper airplanes, flaming screens et al.

If I stop compiz I still have no menu bars in my apps. 
this is the command from window decorator
```
/usr/bin/compiz-decorator
```

I have tried

compiz --replace
metacity --replace
emerald --replace
reinstalling gnome desktop

all of which give me varying degrees of the same problem. Windows managers are a bit confusing to me still, I prefer fluxbox but like the drag and drop options in gnome for working with sound and graphic devices.

---

### Post by gettinoriginal on 2009-06-24
hmmmmmmmm, strange, do you have compiz-fusion-icon installed ??  That allows you to better control your window decorator and window manager.  Once it is installed, it is in Applications > System tools, and when selected will show up in your Notification area of your panel.  Right click on it, and make your selections.  :P  If that does not work, go to CCSM and check your window decoration settings, see screenshot:
[ATTACH]118785[/ATTACH]

---

### Post by SteveNorman on 2009-06-25
Been gone for a bit, Thanks for the reply, I dont have the icon installed, I tried and it didnt install properly. I may be missing some libraries. I will probably just get rid of compiz and re-install it. Does anyone know what config files need to be deleted to get back to a fresh installed, pre configured gnome desktop?

---

### Post by SteveNorman on 2009-06-26
the Icon didnt anything

---

### Post by gettinoriginal on 2009-06-26
Ok, try this:
F2 and type ```
gksu nautilus
```you are prompted for your password, the window opens
Then select the -->view -->reset to defaults within the nautilus window.  
Close window and open an app to see if it's fixed.

---

### Post by SteveNorman on 2009-06-28
It didnt work. I suspect compiz is to blame. Is there a configuration file for gnome?

---

### Post by mcduck on 2009-06-29
> **SteveNorman said:**
> It didnt work. I suspect compiz is to blame. Is there a configuration file for gnome?

I doubt that Compiz has anything to do with this, it's only a window manager and has no control over what happens inside the window. Still, if you want to confirm this, run "metacity --replace" to switch to Gnome's default window manager.

Have you, perhaps, tried (or installed) the mac-like menubar applet ([http://ubuntuforums.org/showthread.php?t=241868]("http://ubuntuforums.org/showthread.php?t=241868&highlight=toolbar")) or something like that? That's the only way I've ever seen people being able to remove the toolbar from programs..

---

### Post by SteveNorman on 2009-06-29
Ive never messed with the mac menu bar, maybe I need to re-install metacity.

With both emerald and metacity I have no menu bars at all.

---

### Post by mcduck on 2009-06-29
> **SteveNorman said:**
> Ive never messed with the mac menu bar, maybe I need to re-install metacity.

With both emerald and metacity I have no menu bars at all.

Nope, window manager still shouldn't have anything to do with what happens inside the window.

Since it works in other desktop environments, it must be something in Gnome. Has it always been like this, and if not, when did the problem occur and what did you do before it?

edit: What happens if you press F10 (the default keyboard shortcut to access menubar)? Have you tried some other GTK theme? Do you have a ~/.gtkrc-2.0 file and if you do, what's in it?

---

### Post by SteveNorman on 2009-06-30
To be honest I dont remember what I did prior to losing them, but I thought I was messing with compiz. I switched back to fluxbox shortly thereafter, and have been using it until this upgrade to 9.04. Now I am having problems mounting things so would like to be able to use gnome and its auto-mounting devilry till I get around to re fstabing everything. 

 f10 does nothing.

Its definitely gnome, and to clarify its in my applications that are open where the bar should read File, Edit View History etc. My panel menu bar is just fine.

---

### Post by SteveNorman on 2009-07-03
man, no-one knows how to reset gnomes defaults?

---

### Post by greggus on 2009-07-09
I have the same problem. 
Menu bar is visible in Firefox but not in GNOME-like apps.
It's almost fresh install...
Any ideas?

---

### Post by SteveNorman on 2009-07-11
seems there is no solution for this. The Gods hate us.

---

### Post by SteveNorman on 2009-07-11
I wonder what deleting .gnome will do,

---

### Post by SteveNorman on 2009-08-24
deleting .gnome* fixed it on reboot.

So there

---

### Post by andrea000 on 2009-08-24
sounds a little like the bug at workspace plugin in 
compiz open compiz go to workarounds plugin and
disable legacy fullscreen support if it happens again.
That may fix it if it's the same bug.

---

### Post by SteveNorman on 2009-08-24
so far so good, I will try that bug fix if it happens again, thanks!

---

### Post by bartman2589 on 2009-09-28
:confused:

I've just encountered this problem too, I've tried renaming my .gnome folder within my home folder (renamed as opposed to delete so that I could restore it if needed), and unfortunately the problem still exists, applications like Firefox and Thunderbird and any KDE applications I open from within GNOME all have the appropriate 'File, Edit, View, etc...' menus however it seems that all native GNOME apps (Nautilus, Synaptic, Gedit, and many others) no longer have these menus, does anyone have any further suggestions (is there maybe a different file I need to edit or delete)?

Thanks in advance,
bartman2589



EDIT: Nevermind I finally found out it was because of Global Menu, I had to reload the Global Menu applet and uncheck the 'Apply to GTK Menus' option, the weird thing is I don't remember ever enabling that feature, I admit I went through synaptic and installed a number of applets so that I could check them out and I tried the Global Menu applet but didn't care for it so I removed it from the Gnome panel, evidently it doesn't restore the settings that it changed when it's removed.

---

### Post by ruth willis on 2009-10-03
hello bartman,

have had same problem lost my menu bar for applications,have got ubuntu  recently installed on pc  could you explain in simpleton terms how  I can  retreived it ,
 :confused:  thanx Rozella

---

### Post by bartman2589 on 2009-10-03
Hi Ruth,
In my case I had  Global Menu (and the Global Menu panel applet) installed, before I uninstalled it I right clicked on it on the applet on the Gnome panel and chose 'preferences' then on one of the tabs there were a bunch of checkboxes (can't remember really if there were multiple tabs or even what the names of the tabs were), I unchecked all of the checkboxes (I think there was an apply button, if so click that then either OK or Close, sorry I didn't really pay much attention to the layout on the preferences window), once I had unchecked all of the checkboxes and closed the preferences window I then right clicked on the applet again and chose 'Remove from panel', then I started the Synaptic Package Manager (as root, either by using a terminal and entering 'gksudo synaptic' or by choosing it from the main menu) and searched for 'globalmenu' in the 'ALL' category on the left side of synaptic, in my case I recieved 4 results with the following package names:

gnome-globalmenu-common
gnome-globalmenu
xfce4-globalmenu-plugin
gnome-applet-globalmenu

I then marked all currently selected packages (out of the search results) for removal choosing 'Mark for complete removal' then chose 'Apply'.

You may need to close and reopen your apps to get the menu redrawn by the operating system, or possibly even may need to restart your computer.

NOTE: If you would rather not get rid of Global Menu (I don't know if you are using a different menu applet or not, such as GnoMenu (a skinnable graphical application menu, with skins similar to the 'Start' menu in Windows and other operating systems), or one of the 2 'Main Menu' applets (one of which is very much like a simplified Windows 'Start' menu) but if you are you should be able to uncheck one of the currently checked items in the preferences for the gnome panel applet to get your menus to show up again in your applications (I didn't care for Global Menu so I chose to make sure I undid all of the changes that had been made before I uninstalled it).

Hope this helps.

Good Luck,
bartman2589

---

