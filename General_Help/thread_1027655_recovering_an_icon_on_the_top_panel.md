---
title: "recovering an icon on the top panel"
date: 2009-01-01
forum: General Help
---

### Post by farrinux on 2009-01-01
Ok I got stupid and deleted my WLAN connection icon on my top panel in gnome.  Tried to find it in the "Add to Panel" menu area but it is not there.  Can any one please tell me where I might find the app and how to put the icon back on the panel?  Thanks

Kev [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by Elfy on 2009-01-01
Try - right click panel, Add to panel - Notification Area

---

### Post by 2hot6ft2 on 2009-01-01
No network manager applet on your toolbar?

If not:

System->Preferences->Sessions

Go to "+ Add"

The fill in the fields as follows:

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

And click "Save"

Then logout and log back in to and see if you have applet on your tool bar.

---

