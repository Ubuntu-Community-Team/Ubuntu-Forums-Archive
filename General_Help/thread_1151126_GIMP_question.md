---
title: "GIMP question"
date: 2009-05-06
forum: General Help
---

### Post by DarkLordPonder on 2009-05-06
Hey all. I'm not entirely sure if this is the right forum, but GIMP doesn't seem to have a support board and it's designed for Linux and Ubuntu, so I thought I'd give a try asking here. Apologies if this is incorrectly located.

For some reason when I open GIMP, it only opens one window. It doesn't open the image manipulation window or the right-hand tool window. It only opens tips and the left-hand tool window. So the only way I can access my brushes or paths etc. is through drop-down windows.

Any way I can fix this?

Thanks,
~DLP

---

### Post by pantone186 on 2009-05-06
On the top menu look for

window > recently-closed-docks

will re-enable a closed panel/dock and when gimp is restarted the docks will remain open



windows > dockable-dialogs

will open a panel/dock



There is a multimedia forum which is probably more appropriate for this type of question

---

### Post by Megrimn on 2009-05-06
Another solution is that when you have that one gimp window open, **hit the tab button** on your keyboard.  

In gimp 2.6 it toggles those other windows, which is actually quite useful if you have a big project or a tiny screen.  Or maybe both.

---

### Post by DarkLordPonder on 2009-05-06
The box I have doesn't have a "windows" button.

My version is 2.0

Another weird thing... normally GIMP has all its windows open on the same layer so that if you click on one of them the others are also made prominent. It's not doing that either... I dunno what the deal is. This is an inherited computer basically, so I dunno what weird settings have been put on this.

---

### Post by Megrimn on 2009-05-11
Well, maybe you might just want to download the latest version, since that may clear up your problems in general.  

The latest version should be in the Ubuntu repositories, pretty easy to download by opening a terminal and typing this:
```
$sudo apt-get install gimp
``` 
or just by going into "add/remove programs" and searching for it, if you prefer GUI. If you are running anything earlier than 8.04, Gimp 2.4 is the latest available installment in the repositories.  Anything 8.10 and later has Gimp 2.6.

You can also find the source code on [http://www.gimp.org/](http://www.gimp.org/)
They won't have any .debs, but if you are running mac or windows, it will have an installer you can download.

On the other hand, I find it hard to believe that you would be running "gimp 2.0."  There should be a version number on the splash that pops up before the program starts.  If you can get into the "Help > About" menu it would tell you as well.  I know that Gimp runs on GTK+ 2.0, and that some of the folders inside of gimp are labeled 2.0.  
I suppose it is conceivable, if your computer hasn't been updated in the last 5 years, more or less.  If that, then maybe your whole computer needs to be updated or something.

---

