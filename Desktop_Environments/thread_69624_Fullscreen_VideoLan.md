---
title: "Fullscreen VideoLan"
date: 2005-09-27
forum: Desktop Environments
---

### Post by cypher35 on 2005-09-27
I assume there are other members here use VideoLan client as one of their media players...  Has anyone been able to get it to produce fullscreen output?

The closest i've found is a setting buried within the module preferences.  

*Settings->Preferences->Modules->video output->xvideo*

Then i select the "Advanced options" checkbox and a couple of options appear.  One of them is labeled "Alternate fullscreen method".  Apparently, it has two settings, one is to just appear in a maximised window (my current problem), and the other is to bypass the windowing system altogether.

I decided to try the ladder, but when i go to fullscreen mode, the window sorta zooms in and VideoLan dissapears from both the screen and the taskbar (i assume it crashes, but i don't get any sort of notification).  Does this have anything to do with my other settings?

If it matters, i am using an ATI card with the fglrx driver set up, the output of fglrxinfo displays my card correctly (if that means anything), and the Kmenu entry for VideoLan is labeled *"VLC for Gtk+"* whatever that means...


Any help would be greatly appreciated
-cypher

---

### Post by beefsprocket on 2005-09-27
Umm, all I do is double click or right click and selsect fullscreen. Which video module are you using? Mine is set to default but you may have to choose a specific output module depending on your system (though with my 9600 mobile I don't have to change anything).

---

### Post by cypher35 on 2005-09-27
could it have something to do with the fact that i'm running a 64bit system?  perhaps the latest version of videolan is not set up for amd64 and i got an outdated binary?

---

### Post by beefsprocket on 2005-09-27
I don't know whether there is a 64bit version. Which version are you using? Have you tried using the vlc repositories?

[http://www.videolan.org/vlc/download-debian.html](http://www.videolan.org/vlc/download-debian.html)

---

