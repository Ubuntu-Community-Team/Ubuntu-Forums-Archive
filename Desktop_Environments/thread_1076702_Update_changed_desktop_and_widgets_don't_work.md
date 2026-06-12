---
title: "Update changed desktop and widgets don't work"
date: 2009-02-21
forum: Desktop Environments
---

### Post by abovett on 2009-02-21
I'm running Kubuntu Intrepid. I updated via aptitude today:

```
sudo aptitude update && sudo aptitude dist-upgrade
```

There were a lot of updates - more than I expected, including something to do with SQL (I'm not to the best of my knowledge running an SQL server) and some didn't install first time, but did when I re-ran aptitude.

However, when I rebooted it seemed like I was in a new operating system! The login screen had changed, the desktop theme had changed, the folder view widgets on the desktop had different control bars, and most of the other widgets don't work. I have errors like:

"Could not find requested component: <name>"

where <name> is "frame", "plasma_applet_notes" etc.

Anyone know what's going on? Lots of things aren't working right - the systems seems pretty much trashed. Have there been some bad updates or is it just my system? The way things are going I'm going to have to reinstall :(

TIA

Andy

---

### Post by myrddinemrys on 2009-02-22
Same problem here.  I like the look of the new KDE 4.2, but the update messed up the widgets.  How do we get them working again?

---

### Post by abovett on 2009-02-22
In the end I decided I had too many problems and reinstalled. Whilst setting things up again I discovered that the extra updates which messed things up before were only offered if I had the backports repository enabled. So maybe I unwittingly updated to KDE 4.2? (I didn't check before reinstalling).

It seems to me that something must be wrong with the repositories though - I had not installed anything from backports, and surely simply enabling the repository shouldn't cause a whole load of new packages to be installed? It seems to me that there's a dependancy error somewhere.

Anyway, I'm now running without the backports repository enabled (I wasn't using anything from it anyway) and everything seems OK.

---

### Post by myrddinemrys on 2009-02-22
Yeah, the update had a hiccup (not disastrous, I just did a 'sudo apt-get -f install' and then a 'sudo aptitude update' and 'sudo aptitude safe-upgrade' to finish the update).

And yes, it is KDE 4.2 that it's updated to.  I'm going to stick with it since I like 4.2.  But would someone please help me get the widgets installable again?  I know broken widgets are *not* a normal 'feature' of 4.2.

---

### Post by txcrackers on 2009-02-22
Not all widgets that were available in the repos have been re-built to work with 4.2 as of yet.

---

### Post by Homie Bongo on 2009-02-22
My desktop got messed with the upgrade too!

After I login to my desktop all I see are white and grey boxes. My widgets do not work and Plasma panel is all gone. I cannot launch the run application dialog. Nonetheless some other apps (MoBloquer) seem to start in the background.

I had 4.2 already, I'm using these extra repositories:

deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

Can anybody help, please? I don't want to reinstall

---

### Post by myrddinemrys on 2009-02-22
FIXED!  For some reason, the KDE 4.2 update removed the old widgets but did not install the new package 'kdeplasma-addons' package.  A simple```
sudo aptitude install kdeplasma-addons
```installed the 4.2 widgets back.

Also, the update removed Kate but did not install the new version.  If you use Kate a lot (like I do), you'll want to install it:```
sudo aptitude install kate
```

And *who knows* what else was removed instead of updated!  Bad call, Canonical!  A bit more testing of next time, please.

But I guess that's the risk we take enabling the "backports" repository in the first place.

---

### Post by txcrackers on 2009-02-22
> **myrddinemrys said:**
> 
And *who knows* what else was removed instead of updated!  Bad call, Canonical!  A bit more testing of next time, please.

But I guess that's the risk we take enabling the "backports" repository in the first place.
Your second paragraph is more accurate than the first... these things are labelled experimental for a reason, y'know. :P

---

### Post by Homie Bongo on 2009-02-22
There are no uninstalled upgrades and I don't miss kdeplasma-addons either on my system...
The widgets say they cannot be found.

---

### Post by myrddinemrys on 2009-02-23
Yeah, your problem seems a bit different than the problem I was having.  For me, the missing widgets were fixed by installing the kdeplasma-addons package (they didn't show up as a missing upgrade for me either).

I found what was missing by doing an aptitude search:```
sudo aptitude search plasma
```

It showed a list of plasma related packages.  The ones listed with a 'c' code mean that the config files already exist, but for some reason the package is not installed anymore.  For me, the kdeplasma-addons package was marked 'c'.  So it looked like it had been removed.  That's why (after reading the description of the package in Adept) I installed it.

You might try doing a aptitude search on 'plasma' or 'widgets' and see if there are any packages listed with a 'c' code.  Those *may* be your missing packages.

However, they could also be old 4.1.4 packages that have been replaced by 4.2 packages.  So check the version #s carefully in Adept before installing.

---

### Post by tux_rocker on 2009-02-23
I managed to fix most of the KDE 4.2 upgrade mess myself. But now the keyboard shortcut for the program starter menu doesn't work anymore. The other keyboard shortcuts work.

This is quite bad for me, if I can't manage to fix it I'll switch to GNOME :(

---

### Post by myrddinemrys on 2009-02-23
> **tux_rocker said:**
> This is quite bad for me, if I can't manage to fix it I'll switch to GNOME :(I agree this upgrade was bad, but going to GNOME's a bit extreme.  If it were me, I'd go back to KDE 4.1 and wait til Jaunty (2 months away) to get KDE 4.2.  At least then you'd know it would work.

---

### Post by Monsieur Gonzalez on 2009-02-23
Hi!

Take a look at the contents of the file kglobalshortcutsrc (folder .kde/share/config), my entry for Run command looks like this (yours might change a little, spanish here) : 
Run Command=Alt+F2,Alt+F2,Ejecutar orden.

Don't give in to the dark side, stay with KDE!!! ;)

---

### Post by tux_rocker on 2009-02-24
> **Monsieur Gonzalez said:**
> Hi!

Take a look at the contents of the file kglobalshortcutsrc (folder .kde/share/config), my entry for Run command looks like this (yours might change a little, spanish here) : 
Run Command=Alt+F2,Alt+F2,Ejecutar orden.

Don't give in to the dark side, stay with KDE!!! ;)

I was talking about the application starter menu - or that's what I suppose it's called in English. Not the "run command" dialog. But I now use the "run command" dialog and I see that it's actually much better than the application starter :-). The name "run command" is a bit of an understatement for what it does.

Anyway, when I look at my kglobalshortcutsrc I do see this line in the plasma section:

```

Activate Programmastarter Widget=Ctrl+Space,Ctrl+Space,Programmastarter

```

which is suspect to me because there's Dutch ("Programmastarter") on the left hand side of the equals sign. Perhaps Plasma doesn't recognize the line for that reason. Can anyone with a KDE configured to US English look how this line looks on his/her system? -- edit: oh well, I can also create a new user and see how the line looks in the home dir of that user.

---

### Post by Monsieur Gonzalez on 2009-02-24
Great to be of help, even if I was mistaken about what you were trying to fix !!!

I agree, Krunner (run command) is a very useful evolution from the kde3 version, you can send emails, search for files, bookmarks, use it as a calculator...

---

