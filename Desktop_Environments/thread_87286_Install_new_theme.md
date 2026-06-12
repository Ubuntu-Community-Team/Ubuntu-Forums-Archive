---
title: "Install new theme"
date: 2005-11-07
forum: Desktop Environments
---

### Post by Captain Nemo on 2005-11-07
**Quick question:**

If I want to install a new theme (GNOME) I am asked to provide a file to store it. The help-topic is not really helping me. It says I have to use a file extension tar.gz

I tried that but got an error -wrong file format.

What is the right way to do such a simple thing?


Thanks!
:confused:

---

### Post by endersshadow on 2005-11-07
Are you using the Theme Manager to install the theme?

Also, can you give a link to the file which you're trying to install?

You should be able to go to the System Menu>Preferences>Theme, click the "Install Theme" button, select your *.tar.gz file and it should install, unless the theme isn't really a theme.  Providing some more info on what you're trying to install and how would be helpful.

Also, this should probably be moved to Gnome Desktop Support.

---

### Post by 23meg on 2005-11-07
You can also just drag and drop the tar.gz file onto theme manager and the theme will appear in the appropriate section in there. Some themes can have variants (different colors etc.) in one archive; if this is the case, double click the archive file and you'll see multiple tar.gz files inside it. Extract them to some temporary folder and drag and drop them onto theme manager individually.

---

### Post by audax321 on 2005-11-07
And I also want to add that to manually install the theme you can just extract it  and put the extracted directory in /home/username/.theme/

The reason I say this is because, as people get more and more dependent on GUI based ways of doing things, they forget how simple it is to do certain tasks manually and I think that is one of the Gnome's strong points:

  e.g. to add to the Create New menu: put templates in /home/username/Templates
        to install icons: extract to /home/username/.icons
        to install a theme: extract to /home/username/.themes
        to make a script accessible from right click: put it in /home/username/.gnome2/nautilus-scripts

Sorry to go off on a tangent but I was just using KDE on my other computer and KDE makes the above (except for the icons) a real pain to do.

---

### Post by RAOF on 2005-11-07
Or, if you want to use a cool program to browse the themes on art.gnome.org, preview, download them and install them automatially, I suggest installing "gnome-art".  Search for it in synaptic, or "sudo apt-get install gnome-art" at a terminal.

Then you can find it under System->Preferences->Art Manager.
Warning: If you're on dialup, it will probably be too slow.

---

