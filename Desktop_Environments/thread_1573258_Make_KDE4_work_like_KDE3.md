---
title: "Make KDE4 work like KDE3"
date: 2010-09-12
forum: Desktop Environments
---

### Post by chip616 on 2010-09-12
This is a kludge, but I have discovered the following:

It is possible to adjust the KDE4 desktop to the way 3.5 works, but you have to create desktop shortcut icons by hand....

I am using Kubuntu 10.04 with KDE 4.4.2, and I have set System Settings | Desktop | Multiple Desktops | Different activity for each desktop. That allows me to run a different background (wallpaper) for each desktop. This works as it did in KDE3.5.

With the above settings, however, I can only create desktop icons that link to applications by navigating the Kmenu, and right-clicking the program, and selecting "Add to desktop".  The bad thing is that regardless of which desktop you are in, the icon gets created in desktop 1, and desktop 1 only.  I have found no way to move them to another desktop afterward, though I am still hoping for a solution on that.

The 'trick' to getting KDE4 to work like KDE3 is to right click the desktop you want to change, select "Folder View Activity Settings", then click "Activity" and change the "type" from Desktop to "Folder view".  The default folder to view is the /home/username/desktop folder, just like in KDE3.

Once that is done, the right-click context menu for that desktop changes, giving some additional options.  One of those new options is "Create new", then "Link to Application".  From there, one can create, by hand, a link to the application much like one could in KDE3.5, including the selection of the icon representing the program (either application icons or 'other icons'), the path, the working directory, the name appearing under the desktop icon, etc., etc.  Just like in KDE3, there is a programname.desktop file created in the /home/username/desktop folder,  which contains the information for the desktop shortcut.

The expanded right click context menu also has the familiar options of aligning the icons to a grid, and so on.

Here is the interesting part:  Any desktop that is set up for folder view will now show ALL the shortcut icons that you created by hand -- just the same as in KDE3.  The /home/username/desktop folder contains all of these shortcut files by default, so any desktop that is set up for folder view sees the same default folder, and therefore shows the same shortcut icons.

In KDE4 it appears that the default folder can be changed.  Ordinarily, it is /home/username/desktop. I tried creating /home/username/desktop1, /home/username/desktop2, /home/username/desktop3 and so on for each desktop, and then editing the default folder for each desktop.  KDE4 ignored my efforts and continued to display only what was in /home/username/desktop in each of the desktops.

In any case, while it is a kludge, it seems that KDE4 can be made to work like KDE3 in the way it displays shortcut icons and program links.

Frank.

---

