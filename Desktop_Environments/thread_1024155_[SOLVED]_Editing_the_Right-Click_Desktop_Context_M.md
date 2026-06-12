---
title: "[SOLVED] Editing the Right-Click Desktop Context Menu in KDE4"
date: 2008-12-28
forum: Desktop Environments
---

### Post by Illydth on 2008-12-28
The subject line says most of it: I'm simply trying to add a single item to the Right-Click Context menu on the KDE4 Desktop.  

I cannot begin to tell you how many different Google searches I've done to try to find this.

This CANNOT be that hard.  Fedora 9/10, as shipped, have "konsole" as a right click item at the top of the KDE4 Desktop Right-Click Context menu...right click on the desktop, and boom "Konsole" is the first option.  

For the LIFE of me I cannot find where the heck this menu is built from.  Searching for "Leave" "Run Command" or "Lock Screen" nets me nothing useful.  Using Locate and xargs grep across the entire /usr/share and /usr/share/kde(4) provides me nothing useful.  As far as I can tell someone at the fedora dev team waved a magic wand and said a spell to get konsole to appear on that menu cause searching a Fedora and an Ubuntu system I simply cannot find where that menu is built from.

And the sad part here is that no one ELSE on the internet seems to know either. :confused:

This simply cannot be that hard, it's got to be a simple text file somewhere.  

Help?  Anyone with any knowledge what-so-ever on how to configure the desktop right click menu on KDE4?  Even information on what directores contain the KDE4 files would be helpful (I know /usr/share/kde4 and ~/.kde are there others?)  Anyone have an idea who might know or where I might better post to get an answer?

*Frustrated*

--Illydth

---

### Post by jacksaff on 2008-12-28
KDE have their own forums now and I would suggest asking there.
There are lots of things in KDE4 that do not yet have a GUI for them but which the underlying code is capable of. Unfortunately as the code is so new you need to ask people who are really knowledgeable about it to get an answer.

---

### Post by Illydth on 2008-12-29
Just to xref to valid information for searches and such:

[http://forum.kde.org/editing-right-click-desktop-context-menu-kde4-t-22508.html](http://forum.kde.org/editing-right-click-desktop-context-menu-kde4-t-22508.html)

Basically the right click desktop menu is hard coded into the code (svn link follows) in the "DefaultDesktop::contextualActions()" function.

[http://websvn.kde.org/trunk/KDE/kdebase/workspace/plasma/containments/desktop/desktop.cpp?view=markup](http://websvn.kde.org/trunk/KDE/kdebase/workspace/plasma/containments/desktop/desktop.cpp?view=markup)

RedHat/Fedora have added their own patch (CVS patch link follows) to add Konsole as a right click command in the F9/F10 build of KDE4.

[http://cvs.fedoraproject.org/viewvc/rpms/kdebase-workspace/F-10/kdebase-workspace-4.0.72-plasma-konsole.patch?view=markup](http://cvs.fedoraproject.org/viewvc/rpms/kdebase-workspace/F-10/kdebase-workspace-4.0.72-plasma-konsole.patch?view=markup)

Technically, the answer is to obtain the kde code, apply this patch to it, and rebuild.  As far as I can tell, the patch above ONLY adds the konsole to the menu, the rest of the information in the text at the top seems to be applied to other files and are not included in the patch linked above.

--Illydth

---

### Post by Illydth on 2008-12-29
BTW, is there a good way of changing the title of the thread here to include [SOLVED]?

Update: Never mind, I found it: Click Edit and then "Go Advanced".

---

### Post by Zorael on 2008-12-29
Regarding tagging as solved, merely retitling it won't do the trick once it has replies. You need to do it via the Thread Tools dropdown menu.

---

### Post by quazi on 2009-02-17
While your specific problem may be solved, how is one to add other items to this menu?  Is it not possible for the casual (someone not willing to hardcode) user at this point?  I'd like to try KDE4 as it looks pretty great, but Compiz enables a custom right-click menu and I'm not using KDE just to run Compiz.

---

