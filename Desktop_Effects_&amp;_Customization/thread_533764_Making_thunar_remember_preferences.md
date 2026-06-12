---
title: "Making thunar remember preferences"
date: 2007-08-24
forum: Desktop Effects &amp; Customization
---

### Post by EGR on 2007-08-24
Hi everyone,

Does anyone know how to make Thunar remember one's preferences?
Whenever I edit the preferences or default applications to use for a
file-type, it only remembers for the rest of the current session;
Thunar loads back with all settings to default if I close it.

I tried searching for its configuration files, but can't find them.
(Nothing in /etc/xdg/).

I think I recall having had the same problem with the xfce-terminal, but
I no longer use it.

I'm running Xubuntu Dapper (though with fluxbox instead of xfce) and
using the latest Thunar from the repos.

Thanks!
Eric

---

### Post by bapoumba on 2007-08-24
I'm not having this problem (with Xfce, not sure it makes any difference).
Thunar preferences are in **~/.config/Thunar/thunarrc**, if that can help.

---

### Post by EGR on 2007-08-24
Funny, that directory has an empty folder for xfce but nothing for Thunar.
Find doesn't turn up anything either for thunarrc.
I'm going to try re-installing it, see if changes anything.

---

### Post by bapoumba on 2007-08-24
Here's mine, and other related files ;)
```
isabella@yeti:~ $ locate thunarrc
/home/isabella/.config/Thunar/thunarrc
/etc/xdg/Thunar/thunarrc
/usr/share/doc/thunar-data/README.thunarrc.gz
isabella@yeti:~ $ cat /home/isabella/.config/Thunar/thunarrc
[Configuration]
DefaultView=void
LastCompactViewZoomLevel=THUNAR_ZOOM_LEVEL_SMALLEST
LastDetailsViewColumnOrder=THUNAR_COLUMN_NAME,THUNAR_COLUMN_SIZE,THUNAR_COLUMN_TYPE,THUNAR_COLUMN_DATE_MODIFIED
LastDetailsViewColumnWidths=50,114,50,50,418,50,50,64,214
LastDetailsViewFixedColumns=FALSE
LastDetailsViewVisibleColumns=THUNAR_COLUMN_DATE_MODIFIED,THUNAR_COLUMN_NAME,THUNAR_COLUMN_SIZE,THUNAR_COLUMN_TYPE
LastDetailsViewZoomLevel=THUNAR_ZOOM_LEVEL_SMALLER
LastIconViewZoomLevel=THUNAR_ZOOM_LEVEL_NORMAL
LastLocationBar=ThunarLocationButtons
LastSeparatorPosition=232
LastShowHidden=FALSE
LastSidePane=ThunarShortcutsPane
LastSortColumn=THUNAR_COLUMN_NAME
LastSortOrder=GTK_SORT_ASCENDING
LastStatusbarVisible=TRUE
LastView=ThunarDetailsView
LastWindowHeight=480
LastWindowWidth=903
MiscCaseSensitive=FALSE
MiscFoldersFirst=TRUE
MiscHorizontalWheelNavigates=FALSE
MiscRecursivePermissions=THUNAR_RECURSIVE_PERMISSIONS_ASK
MiscRememberGeometry=TRUE
MiscShowAboutTemplates=TRUE
MiscShowThumbnails=TRUE
MiscSingleClick=FALSE
MiscSingleClickTimeout=500
MiscTextBesideIcons=FALSE
ShortcutsIconEmblems=TRUE
ShortcutsIconSize=THUNAR_ICON_SIZE_SMALLER
TreeIconEmblems=TRUE
TreeIconSize=THUNAR_ICON_SIZE_SMALLEST
MiscVolumeManagement=TRUE

```

---

### Post by EGR on 2007-08-24
It appears that Thunar simply failed to create the relevant files upon
installation. I did manage to edit the preferences by saving your
template in the ~/.config/Thunar folder, and editing that file. Weird
thing is, it still won't remember any changes I make from the menus.  
I guess I'll have to keep to manual editing, but at least *that* works. 

Thanks a lot!

---

### Post by bapoumba on 2007-08-25
You're welcome. Strange it does not work from the GUI.

---

