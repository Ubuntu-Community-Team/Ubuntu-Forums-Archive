---
title: "Konqueror &quot;View Mode&quot; icons not present and no way to add"
date: 2006-06-06
forum: Desktop Environments
---

### Post by Psy-Q on 2006-06-06
It seems that there is no way to get the "View Mode" icons onto the toolbar in Konqueror on Dapper (release). The icons I mean can be used to switch between view modes, e.g. List and Icon views, while managing files. Normally they reside somewhere in the main toolbar. If they're not there, the toolbar configuration dialog usually has them somewhere (verified this on Debian testing). Yet in Dapper, they're nowhere to be found, neither on the toolbar itself nor in the config dialog.

Might also be this bug: [https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/43949](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/43949)

Is there a workaround in the meantime? These are very important and useful icons.

---

### Post by magnusbb on 2006-06-15
I second that. I've been looking for this for quite some time now, and it really makes the Konqueror more difficult to use as a file manager.

---

### Post by padre999 on 2006-06-15
[QUOTE=Psy-Q]It seems that there is no way to get the "View Mode" icons onto the toolbar in Konqueror on Dapper (release). The icons I mean can be used to switch between view modes, e.g. List and Icon views, while managing files. Normally they reside somewhere in the main toolbar. If they're not there, the toolbar configuration dialog usually has them somewhere (verified this on Debian testing). Yet in Dapper, they're nowhere to be found, neither on the toolbar itself nor in the config dialog.

Might also be this bug: [https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/43949](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/43949)

Is there a workaround in the meantime? These are very important and useful icons.[/QUOTE]

I found a fix posted in a german forum: 

[http://forum.ubuntuusers.de/topic/35182/](http://forum.ubuntuusers.de/topic/35182/)

If you have problems reading German: :rolleyes: 

You have to add 

```
<ToolBar newline="false" hidden="false" name="viewModeToolBar" >
<text>ViewMode Toolbar</text>
<ActionList name="viewmode_toolbar" />
</ToolBar>

```
to ~/.kde/share/apps/konqueror/konq-kubuntu.rc

This would make the icons visible just for this user. To make it globally available for all users you have to add it to the file /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror/konq-kubuntu.rc


Don't forget to logout/login after the change.

---

### Post by samwyse on 2007-11-25
I tried the above trick, but in Gutsy it just adds the default Gutsy one button list instead of the three KDE ones displayed here: [http://kde.org/screenshots/images/3.4/snapshot06.png](http://kde.org/screenshots/images/3.4/snapshot06.png).

---

### Post by bailout on 2007-11-25
If you click and hold on the one button you get a drop down menu.

---

### Post by samwyse on 2007-11-25
> **bailout said:**
> If you click and hold on the one button you get a drop down menu.
I know, but changing between icon and list mode is slow with the huge list.

---

### Post by samwyse on 2007-11-26
> **Psy-Q said:**
> Might also be this bug: [https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/43949](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/43949)
I just noticed there's a patch included, which works. It also seems to fix the bug where moving up from viewing an embedded image changed to icon view mode no matter which view mode was selected before.

---

