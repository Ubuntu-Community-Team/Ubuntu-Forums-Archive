---
title: "desktop keeps crashing when renaming folder under folder view plasmoid"
date: 2011-06-17
forum: Desktop Environments
---

### Post by 13east on 2011-06-17
Running kubuntu 11.04x64 w/ xrender and folder-view plasmoid:

I cannot view "open with" for directories on the desktop (but it is visible w/in dolphin file structure) and whenever I try to rename folders on the desktop it crashes and restarts (but the rename is successful and no open windows crash).  

This glitch is reproducible under OpenGL and Xrender; had to switch over to xrender after a recent system update that seems to slow my computer to a crawl after a little time and kept it cause it seems much smoother and crisper.

Is there any way to fix these issues or is there an alternative to the folder-view plasmoid to view a folder content on the desktop that is more stable?

---

### Post by ankspo71 on 2011-06-17
Hi,
One alternative to the folder view plasmoid is to display the icons directly on the desktop by using the folder view layout. 

Right click on your desktop and unlock the widgets if they are locked. Next, right click on your desktop and click on Desktop Settings. When the Desktop Settings window opens, look in the View category for the "Layout:" dropdown menu. Change it from Desktop to Folder View. Then click apply.
Hope this helps.

---

### Post by 13east on 2011-06-17
> **ankspo71 said:**
> Hi,
One alternative to the folder view plasmoid is to display the icons directly on the desktop by using the folder view layout. 

Right click on your desktop and unlock the widgets if they are locked. Next, right click on your desktop and click on Desktop Settings. When the Desktop Settings window opens, look in the View category for the "Layout:" dropdown menu. Change it from Desktop to Folder View. Then click apply.
Hope this helps.

I have the same problem w/ both the plasmoid and the folder view layout.  I cannot view the "open with" option for directories, nor can I rename any files/folder without the desktop crashing and reseting itself, and at times there are issues with deleting files properly from the desktop.  These issues only started recently and trying to remove/reinstall the folderview plasma doesn't do anything to fix the problems (sudo aptitude purge plasma-widget-folderview).

I've been experiencing a lot of problems since a recent major system update.  There have been a lot more than usual system crashes and major performance/graphics issues only recently.  Kubuntu 11.04 was somewhat stable if not completely.  Is there a way to revert my machine back to before the recent update and just wait for the next batch of updates to address these issues?

---

### Post by wildmanne39 on 2011-06-18
> **13east said:**
> I have the same problem w/ both the plasmoid and the folder view layout.  I cannot view the "open with" option for directories, nor can I rename any files/folder without the desktop crashing and reseting itself, and at times there are issues with deleting files properly from the desktop.  These issues only started recently and trying to remove/reinstall the folderview plasma doesn't do anything to fix the problems (sudo aptitude purge plasma-widget-folderview).

I've been experiencing a lot of problems since a recent major system update.  There have been a lot more than usual system crashes and major performance/graphics issues only recently.  Kubuntu 11.04 was somewhat stable if not completely.  Is there a way to revert my machine back to before the recent update and just wait for the next batch of updates to address these issues?Hi, probably not easily, but you should look in your update manager settings and make sure that prerelease updates or not checked.

---

### Post by ankspo71 on 2011-06-18
Hi,
There is one alternative to the folder view plasmoid itself located here:
[http://gtk-apps.org/content/show.php?content=102890](http://gtk-apps.org/content/show.php?content=102890)
It requires screenlets to be installed and running in the background. I can't say how well it works on the KDE desktop though. It should work fine as long as screenlets works well with Kwin's compositing though.


Unfortunately, undoing system updates as a whole is pretty much impossible to do, but sometimes there is the possibility to downgrade an individual package, because sometimes there are multiple versions to popular (or known to be troublesome) packages in the repositories.

Are you still able to open Dolphin and navigate to your desktop to edit and rename the files? If Dolphin is being a problem too, you could install a second file manager to use (Nautilus, Thunar, Pcmanfm, etc) until the issue is resolved through the next batch of updates. You can then go to System Settings > Default Applications > File manager, to choose the default file manager used to automatically open when you click on the folders. This won't fix the file manager features of the desktop itself, but at least you can open your desktop folder with it.

Hope this helps.

---

### Post by 13east on 2011-06-18
> **ankspo71 said:**
> Hi,
There is one alternative to the folder view plasmoid itself located here:
[http://gtk-apps.org/content/show.php?content=102890](http://gtk-apps.org/content/show.php?content=102890)
It requires screenlets to be installed and running in the background. I can't say how well it works on the KDE desktop though. It should work fine as long as screenlets works well with Kwin's compositing though.

Screenlets installs a lot of gnome dependency libraries along with it (129 new packages @ 203 mb) so I'm going to hold off on this option for now anyway.
----------------------
> **wildmanne39 said:**
> Hi, probably not easily, but you should look in your update manager settings and make sure that prerelease updates or not checked.

&

> **ankspo71 said:**
> Unfortunately, undoing system updates as a whole is pretty much impossible to do, but sometimes there is the possibility to downgrade an individual package, because sometimes there are multiple versions to popular (or known to be troublesome) packages in the repositories.

I had a feeling this would be the answer... oh well... this'll teach me not to be too eager to keep experimental and beta repositories active.
----------------------
> **ankspo71 said:**
> Are you still able to open Dolphin and navigate to your desktop to edit and rename the files? If Dolphin is being a problem too, you could install a second file manager to use (Nautilus, Thunar, Pcmanfm, etc) until the issue is resolved through the next batch of updates. You can then go to System Settings > Default Applications > File manager, to choose the default file manager used to automatically open when you click on the folders. This won't fix the file manager features of the desktop itself, but at least you can open your desktop folder with it.

Hope this helps.

Fortunately the plasma desktop seems to be the only thing affected by system glitches; I can launch Dolphin and work with files/folders properly from within it.
----------------------
Thank you everyone for you very helpful responses.

---

### Post by wildmanne39 on 2011-06-18
Hi, your welcome, sorry we could not tell you a easy fix, I had my system set to update the prerelease also, but I changed that when my system started acting up, I also run oneiric so that is the system I test on, I want at least one to be stable.

---

### Post by christopher.wortman on 2011-06-18
Do you have over 4gig of ram? If not I suggest using 32 bit version of the OS as the issue does not seem to persist on my desktop as you say it.

---

### Post by 13east on 2011-06-18
> **christopher.wortman said:**
> Do you have over 4gig of ram? If not I suggest using 32 bit version of the OS as the issue does not seem to persist on my desktop as you say it.

I have 4gigs of ram and 4gigs of swap-drive.

I know there isn't too much of a difference between 32bit and 64bit OS w/ respect to performance as of right now, and 32bit is more stable in most cases... but I paid for x64 hardware so I want use it.  But if the glitches remain this extreme than I might have to take your advice.

---

### Post by 13east on 2011-06-19
> **wildmanne39 said:**
> Hi, your welcome, sorry we could not tell you a easy fix, I had my system set to update the prerelease also, but I changed that when my system started acting up, I also run oneiric so that is the system I test on, I want at least one to be stable.

I just did a clean reinstall of kubuntu back onto my machine.  This time I kept out the proposed, unsupported, experimental and beta repositories,  I'm still seeing the same issues I had before and am starting to notice one major new glitch: still can't rename folders or view "open with" on the desktop, and now I can't seem to be able to run fullscreen streaming videos under OpenGL with out the computer crashing.  I had the same issue before but thought it got fixed when I suspended desktop effects for fullscreen apps under settings.  Xrender seems to handle fullscreen video alright.

---

