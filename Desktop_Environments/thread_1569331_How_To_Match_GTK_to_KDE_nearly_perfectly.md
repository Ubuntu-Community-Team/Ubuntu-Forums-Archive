---
title: "How To: Match GTK to KDE nearly perfectly"
date: 2010-09-06
forum: Desktop Environments
---

### Post by Alan James on 2010-09-06
Attached is an image of what I will be describing. The top window has the &#8220;Radial Gradient&#8221; (the default in KDE) the bottom has a solid background. I think the bottom matches better.

To correct a specific application in KDE 4.4 go into &#8220;System Settings.&#8221;
Click on Appearance. 
In the side pane click on &#8220;Windows&#8221;. Then click on the &#8220;Window-Specific Overrides&#8221; tab. 
Click &#8220;Add&#8221;, then &#8220;Detect Window Properties.&#8221; A cross-hair appears. 
Click on the GTK application you want to re-theme. 
A dialog box will pop up, just click &#8220;OK.&#8221; 
You are returned to the previous screen. 
Check &#8220;Background Style&#8221; then select &#8220;Solid Color&#8221; from the drop down. 
Click &#8220;OK&#8221; then click &#8220;Apply&#8221;. 

The gradient is gone and the GTK application looks more at home in KDE.

My question is, does anyone know of a way to do this for **all** GTK applications at once?

---

### Post by Alan James on 2010-09-07
Does anyone know of this command?

---

### Post by ankspo71 on 2010-09-13
Hi,
What about doing a little theme customizing... more specifically configure the Oxygen window decoration (or choose another decoration) and use QtCurve as your style?

First, The Oxygen window decoration has an option to turn off the gradient background. 
In KDE 4.5.1 (the version I am using), I can go here to do that:
System Settings > Workspace Appearance > Window Decorations > Select the Oxygen window border > then click on configure Decoration > Fine Tuning > Background Style:-> "Solid Color". The location to do this is probably different in KDE 4.4x so just look for the section where you switch window decorations then click on the Configure Decoration button.

This creates another problem though, because the Qxygen style (KDE's default window theme) is still using a gradient. This is where I would recommend using any of the QtCurve KDE styles. QtCurve is VERY  configurable and even feels lighter on my system compared to Oxygen. The QtCurve style can also be used in GTK applications also. If you have QtCurve 1.5 or greater installed, it also supports window transparency in KDE applications. Some people have uploaded some really good QtCurve styles at KDE-look.org too. You will need to install QtCurve more than likely, but it is available in the Ubuntu repositories.

To switch from Oxygen to QtCurve styles, go to System Settings > Application Appearance > Style > Widget Style: -> "QtCurve". To configure the style to your liking, you can click on the configure button right next to the QtCurve selection. 

To configure your gtk applications to use QtCurve, go to System Settings > Application Appearance > GTK Appearance, and make sure the QtCurve option for the Widget Style is selected,

Aurorae window decoration themes can also be used, but there aren't too many to choose from at KDE-look.org. There are some really nice ones there though. The Aurorae window decorations can be found in the package called "kdeartwork" metapackage.

---

### Post by ankspo71 on 2010-09-13
Hi again,
I'm adding an image to show how well the QtCurve styles match GTK and KDE application windows and window decorations. I am also showing the Oxygen window decoration with the gradient background turned off. The applications shown are; torrent search, firefox, dolphin, lastfm client, konsole and pitivi.

---

