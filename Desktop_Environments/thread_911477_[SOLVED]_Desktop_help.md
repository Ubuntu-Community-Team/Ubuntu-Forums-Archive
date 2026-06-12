---
title: "[SOLVED] Desktop help"
date: 2008-09-05
forum: Desktop Environments
---

### Post by semitone36 on 2008-09-05
Hello everyone

Im in the process of trying to customize my desktop all nice like the millions of screenshots you'll see around here but im having a few difficulties.

The first thing I noticed was that I DONT have gnome-theme-manager and when I try to install it I get this:

travis@travis-laptop:~$ sudo apt-get install gnome-theme-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-theme-manager

Does that seem odd to anyone? Id like to change the look of my icons but I cant find an "icons" section in any of my other theme programs (appearances, Emerald theme manager)

My other problem is that I cant add desklets.  I have gdesklets installed but every time I open it, it sorta just crashes.  I get a grey window on my screen and when I close it I get an error message that says gdesklets is not responding.  When I open gdesklets through the terminal this is what I get:

travis@travis-laptop:~$ gdesklets
Starting gdesklets-daemon...
Cannot establish connection to daemon: connection timeout
The log file might help in solving the problem.

Please someone help me out, Im giving a persuasive speech on Linux in a few weeks and Id like my comp to look as impressive as possilbe:)

---

### Post by benerivo on 2008-09-05
I don't think the package 'gnome-theme-manager' exists. For icon changes go to System>Preferences>Appearance then on the theme tab, go to the 'Customise' button and go to 'Icons'.

I'm not sure about gdesklets as i never use them, but i think screenlets are slightly more popular. Check what that log file says. The log is probably in your home folder somewhere, but if you can't find it then look in /var/logs.

---

### Post by semitone36 on 2008-09-05
I couldnt find the log but I tried screenlets and it actually works lol thanks!  As for the icons I found them but how do I add new icon styles?

---

### Post by benerivo on 2008-09-05
The way i do it is to download an icon set from gnome-look such as [this]("http://www.deviantart.com/download/87655584/GNOME_Colors_by_perfectska04.zip") one. You'll download an archive (maybe a tar.gz or a zip file). If you drag the downloaded .tar.gz icon in to the 'System > Preferences >Appearance' window then it will try to install that icon set. Try downloading [this]("http://www.gnome-look.org/content/show.php/Jungle+Green%2BBlack%2BOrange?content=82403") icon theme (it is a tar.gz format) and drag the downloaded icon in to the 'Appearance' window.

---

### Post by semitone36 on 2008-09-05
Those jungle ones worked just fine but for some reason the appearance editor doesnt recognize the other set I downloaded or the first set you sent recommended.  But i guess some success is better than no success.  Thanks for the help!

---

### Post by benerivo on 2008-09-06
It might be because the file you drag and drop in to the window needs to be in tar.gz format. Also, it needs to contain only the icon theme. Some of these downloads contain several themes (maybe two icons themes, maybe an icon theme and a gtk theme). So the download may need to be opened, and the correct tar.gz extracted from it. This is true of the gnome-colours download i linked to. It has several icon themes, and each has to be extracted separately so that it can be dragged and dropped.

---

