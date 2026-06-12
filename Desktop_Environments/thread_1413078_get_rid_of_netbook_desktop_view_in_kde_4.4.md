---
title: "get rid of netbook desktop view in kde 4.4"
date: 2010-02-22
forum: Desktop Environments
---

### Post by mlinchits on 2010-02-22
I chose the netbook view for my desktop and cannot figure out how to change it. It is no longer possible to right click on the desktop to modify its properties or to click on the plasma handle. System preferences does not provide an option to modify the desktop. How can I invoke the desktop settings window which modifies desktop properties (wallpaper, folder view etc.) in this situation?

Thanks

---

### Post by inobe on 2010-02-22
rename **~/.kde4** if you cannot change anything in personal settings.


doing so will reset your desktop to it's default when you first installed 4.4, backup your bookmarks first, your data should be fine, simply show hidden files in dolphin and browse for .kde4 folder, rename it' or even delete it and log out or restart.

---

### Post by Zorael on 2010-02-22
What? It's not necessary to wipe your settings for this; if you read his post he's asking for how to find a dialog, not how to fix a setting not being saved. Further, settings are saved in **~/.kde** (and not **.kde4**) as of Jaunty or something.

> **mlinchits said:**
> I chose the netbook view for my desktop and cannot figure out how to change it. It is no longer possible to right click on the desktop to modify its properties or to click on the plasma handle.
Do you want to change activity settings (wallpaper, type of activity, mouse actions et al), or do you want to change between plasma netbook and plasma desktop?

Merely right-clicking an empty space should offer an option to Configure Search and Launch, or Configure page, or Configure Activity, or Configure Desktop (depending on what the activity is set to be).

To switch between desktop and netbook, you have a drop-down menu at System Settings -> Desktop -> Workspace -> Form factor.

---

### Post by inobe on 2010-02-22
he says there is no right click, it's a bug in 4.4.0 that many have experienced even in opensuse.

---

### Post by Zorael on 2010-02-22
In that sense. I see. Then yes, this sounds like a bug and not user error. Renaming **~/.kde/share/config/plasma-netbook*** would make it recreate your plasma netbook settings from default.

Without knowing what the bug could be, you could also try manually adding the definition for what mouse action the right mouse button should trigger. In **~/.kde/share/config/plasma-netbook-appletsrc**;
```
[Containments][**1**][ActionPlugins]
RightButton;NoModifier=contextmenu
```
By default, containment **1** is the Search and Launch activity, **2** is the panel (plugin=netpanel) and **3** is Page one.

---

### Post by DannyBPNG on 2010-03-15
I ran into the same problem when I set the desktop to the Mandelbrot. My guess is that the applet takes over the desktop space and the right mouse click has no programmed response. Since the mouse wheel zooms in and out, I figure they have not thought about the right click.

So I did the following:

* Edited the following file: ~/.kde/config/plasma-desktop-appletsrc

* Searched for the entry: plugin=desktop

* Within that section I changed the: wallpaperplugin=...
to
* wallpaperplugin=image

* Saved the file
* Logged out and logged back in

Then I had access to the desktop again (could right click on it). See if that fixes the problem.

---

### Post by inobe on 2010-03-15
thanks for sharing that valuable information DannyBPNG and welcome to the ubuntu forums.

---

### Post by murali_sb on 2010-08-19
Don't know if it makes any sense but i had run into the same problem and this is how i fixed it :p -

Go to configure ur desktop -> Look-n-feel -> Multiple Desktops and have atleast 2 desktops enabled. It would also help to enable the option Different activity for each desktop.

Then go to 2nd desktop and click on the cashew to reveal Folder View Activity settings -> Activity -> Change back to folder view.

You'll get back your original desktop, i didn't delete or rename any file.

Now the funny part is inspite of enabling Different activity for each desktop, when i changed to folder view in 2nd desktop it applied to 1st as well. I think this could be another bug, anyway i don't care as long as it worked for me.

BTW I did this on PCLOS 2010 but i'm sure the same settings should be available for kubuntu as well.

Hope this helps.

---

### Post by whalogreg on 2010-08-20
Anyone know the way to do this under gnome?

---

### Post by idef1x on 2011-03-20
> **whalogreg said:**
> Anyone know the way to do this under gnome?
Just install the full ubuntu desktop packages :

sudo apt-get install ubuntu-desktop

and then logout and choose at login the normal desktop...

---

### Post by wizardvamshi on 2012-12-13
> **mlinchits said:**
> I chose the netbook view for my desktop and cannot figure out how to change it. It is no longer possible to right click on the desktop to modify its properties or to click on the plasma handle. System preferences does not provide an option to modify the desktop. How can I invoke the desktop settings window which modifies desktop properties (wallpaper, folder view etc.) in this situation?

Thanks

Hello,

To get back to Desktop Plasma Do the following..

Go to add widgets and select the "KDE application launcher"(if you haven't already added).  

Now search "workspace" ... Select Workspace Type: "Desktop" from the dropdown menu and can revert back to
Desktop Plasma.

If you like to explore a bit more.. just follow the same..choose workspace Type : "Netbook" ;)


-Vamshi

---

### Post by howefield on 2012-12-13
Old thread back to sleep.

---

