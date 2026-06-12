---
title: "gnome+xfce?"
date: 2007-04-27
forum: Desktop Environments
---

### Post by mailbox on 2007-04-27
i installed xfce, and i like most of it, but i'm used to being able to drag-select multiple items on the desktop, dragging images from firefox to the desktop to download them, and having image/movie/text previews in the icons.
is there a way to use gnome to handle the desktop and have xfce take care of the rest?

---

### Post by bapoumba on 2007-04-27
I do not think so. They are environments, and you can run GNOME apps in xfce, or xfce apps in GNOME.
As far as the drag'n drop thing, it's working here, but I do not use it much. So I may have missed something.

---

### Post by x1a4 on 2007-04-27
Hi,

Find GNOME's desktop executable (in Xfce it's xfdesktop, and KDE it's kdesktop).  I looked for if for you but couldn't find it.  Once you locate it do this: 

RClick on the desktop, click 'Desktop Settings' and **un**check 'Allow Xfce to manage the desktop' then click the 'Close' button.  

Press Alt+F2 to open the 'Run' dialog and run GNOME Desktop

Create a .desktop file for the GNOME Desktop in ~/.config/autostart/

Logout, and make sure you checked the 'Save session for future logins' check box.  

Log back in.

---

