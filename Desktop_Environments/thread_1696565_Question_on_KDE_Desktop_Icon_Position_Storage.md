---
title: "Question on KDE Desktop Icon Position Storage"
date: 2011-02-27
forum: Desktop Environments
---

### Post by lariosa42 on 2011-02-27
I'm running KDE4 with the "Folder View Activity" setting turned on.  When I change my display resolution, and then change back, I notice my desktop icons are completely rearranged.  I would like to write a script that saves my old icon positions and updates them later.  Where are the icon positions stored?  

I found out that the positions are logged every few seconds in the "savedPositions" variable in this file:
```

~/.kde/share/config/plasma-desktop-appletsrc
```

However, I don't think this file is read from.  Modifying the positions in the above file and refreshing the desktop does not rearrange the icons.

Google has not been much help.  Does anyone know where the desktop icon positions are stored?

---

### Post by JohStr on 2012-03-01
lariosa42 you seem to be right.
I'm driving KDE4 on Fedora Linux.
The place where the icon positions are stored is the file
~/.kde4/share/config/plasma-desktop-appletsrc
  Inside this file there is a line beginning with
savedPositions=
In my case it shows like this: savedPositions=1,47,Music,501,115,Video,14,256, .....
This means: 
There are 48 Icons on Desktop 1 (I guess),
One icon called Music on xposition 501, yposition 115
One icon called Video on xposition 14, yposition 256
When I vary the Position of Icon Music, the entry in this file is also varied some seconds later.
So I saved this file apart and made the following test.
I varied the position of some Icons and logged out of the desktop.
I copied back the saved file plasma-desktop-appletsrc as root.
After I logged in again, the old icon positions showed up in their original places!
I hope this was helpful to you.

---

