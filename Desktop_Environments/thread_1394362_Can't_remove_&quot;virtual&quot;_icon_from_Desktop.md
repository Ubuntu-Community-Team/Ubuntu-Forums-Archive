---
title: "Can't remove &quot;virtual&quot; icon from Desktop Folder view"
date: 2010-01-30
forum: Desktop Environments
---

### Post by sbalfour on 2010-01-30
I'm on Kubuntu 9.10, with KDE desktop.  On my screen, there is a "Desktop Folder"
inset.   In the inset there is an icon "KTorrent" which I previously found under KMenu/Applications/Internet and selected "Add to Desktop".  It appeared on the edge
of my screen, outside the "Desktop Folder" inset.  So I dragged and dropped it onto 
the "Desktop Folder".  When I mouse over it, it doesn't light up. Clicking on it does
nothing.  There's nothing in the ~/Desktop folder to represent it. It's some kind of 
virtual object.  When I copy Ktorrent.desktop file from /usr/share/applications
/kde4/ktorrent.desktop to ~/Desktop, *another* KTorrent icon appears
with a "!" superimposed on it.  Mousing over the new icon seems to work, but I don't
think what I did is the approved method of getting the icon in the "Desktop Folder" view.

1. How do I get rid of the "!" on the KTorrent icon?
2. How was I supposed to add KTorrent icon to the Folder View?
3. How do I get rid of the "Virtual" , i.e. inert, KTorrent icon from the Folder View?
                                          
                                       Stuart

---

### Post by Zorael on 2010-01-30
I'm trying to reproduce this but I don't get an option to Add to Desktop when right-clicking a menu entry - only Add to Favorites.

Anyway, could the icon simply be *behind* the (translucent) folder view?

As for the "best practice" of creating a launcher for an application, I believe that's right-clicking the folder view space, then Create New -> Link to Application.

---

### Post by sbalfour on 2010-01-30
Thank You sir, you are absolutely correct - the icon is BEHIND the translucent Folder
View.  I've never worked with this plasma stuff before - neither YellowDog, Redhat, Fedora,
Irix or Solaris has anything like it.  I can delete the errant icon after moving the Folder
View out of the way.  And Your method of adding an icon to the Folder View not only
works, but the added icon does not have a "!" on it.  Regards,
                                                                    Stuart

---

