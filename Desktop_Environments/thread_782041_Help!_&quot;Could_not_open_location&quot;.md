---
title: "Help! &quot;Could not open location&quot;"
date: 2008-05-04
forum: Desktop Environments
---

### Post by slick_nick on 2008-05-04
Turns out, SOMEHOW nautilus got uninstalled. Installed it and everything is fine.


Something is wrong with gnome/x: Whatever files/icons I had on my desktop, as well as my wallpaper, have disappeared.  When I try to go anywhere in Places, I get the error:
*Could not open location 'file:///home/slick/Documents' There is no default action associated with this location.*  !!!!

Things were working fine last night, through a reboot (usb devices sometimes lock up my computer, different issue...), I haven't messed with anything since then, and now it's totally screwed.  I have of course tried turning it off and on again. (IT crowd anyone? :) )

At least I can still open Firefox and get a terminal window up, so hopefully with the help our fine community members I can fix this!

Edit: I get the same error if I hit alt-F2 to get the gnome run dialog and type in the location.

---

### Post by p_quarles on 2008-05-05
This sounds like a problem with the configuration settings for Nautilus. Just to test this to make certain, try this: open a terminal window, and type:
```
mv .gconf/apps .gconf/apps-backup
```
Essentially, this renames the directory where Nautilus's settings reside. This will force it to regenerate the default settings. After doing this, try opening up the file manager again and see if it works now.

At any time, you can restore the old (broken) settings by running:
```
mv .gconf/apps-backup .gconf/apps
```
However, first, you may want to compare the old Nautilus file with the new one. open up both of these (and post them here if you need help troubleshooting):
```
.gconf/apps/nautilus/%gconf.xml
```
and 
```
.gconf/apps-backup/nautilus/%gconf.xml
```
Hope this helps.

---

### Post by slick_nick on 2008-05-05
Still broken :(  I wouldn't be too upset if I had to do a reinstall of Hardy but would like to figure this out!

The %gconf.xml in the nautilus folder is blank; there is also a folder called 'preferences' in that folder, with another %gconf.xml; all it has is
```
<?xml version="1.0"?>
<gconf>
        <entry name="navigation_window_saved_geometry" mtime="1209854363" type="string">
                <stringvalue>1279x950+0+25</stringvalue>
        </entry>
        <entry name="navigation_window_saved_maximized" mtime="1209890292" type="bool" value="true">
        </entry>
</gconf>
```

Edit: I just tried saving a picture to the desktop from firefox, and it didn't show up on the desktop. When I right-click and say Open Containing Folder, it brings up a Launch Application dialog, which says "This link needs to be opened with an application".  Also went to System -> Preferences -> Appearance and trying setting a desktop image, to no avail. It is stuck on a sort of flesh-tone right now...oddly it looks lighter than the default color in Appearance?

---

### Post by siegfried78 on 2009-11-03
sudo apt-get install nautilus

;)

---

