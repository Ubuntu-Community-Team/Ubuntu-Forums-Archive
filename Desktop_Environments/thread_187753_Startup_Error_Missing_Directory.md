---
title: "Startup Error: Missing Directory"
date: 2006-06-03
forum: Desktop Environments
---

### Post by kabronkline on 2006-06-03
This problem seems to be fairly simple, but I've done lots of digging and I still can't find the answer. Whenever I log onto Gnome with my user account I receive the error:

"Couldn't find "/home/kabron/Documents/Pictures"

Previously, I had been using a background image stored in that directory; however, I have since stopped using that desktop background and the directory "/home/kabron/Documents/Pictures" no longer exists.

I have explored my Desktop Background tool found at "System>Administration>Desktop Background" but the only images in the list are the default image loaded with Dapper. Can somebody please help?

---

### Post by tonyr on 2006-06-03
Here is a possibility.  The list of background selections is kept in the file
**.gnome2/backgrounds.xml**.  Look in that file and see if there is a line
that contains the directory name.  If it is there, then somehow when you quit
using the background, that entry did not get removed.

---

### Post by kabronkline on 2006-06-03
This didn't seem to help. Here is what my backgrounds.xml file reads:

> <?xml version="1.0"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers>
  <wallpaper deleted="true">
    <name>38316-1.jpg</name>
    <filename>/home/kabron/Personal/Media/Pictures/38316-1.jpg</filename>
    <options>scaled</options>
    <shade_type>solid</shade_type>
    <pcolor>#4E3E29</pcolor>
    <scolor>#7F7F7F</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Ubuntu Lagoon</name>
    <filename>/usr/share/backgrounds/warty-final-ubuntu.png</filename>
    <options>stretched</options>
    <shade_type>solid</shade_type>
    <pcolor>#2C160A</pcolor>
    <scolor>#2C160A</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Ubuntu Lagoon Widescreen</name>
    <filename>/usr/share/backgrounds/warty-final-ws-ubuntu.png</filename>
    <options>stretched</options>
    <shade_type>solid</shade_type>
    <pcolor>#2C160A</pcolor>
    <scolor>#2C160A</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Simple Ubuntu</name>
    <filename>/usr/share/backgrounds/Ubuntu-Simple_Human_1600x1200.png</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#2C160A</pcolor>
    <scolor>#2C160A</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>No Wallpaper</name>
    <filename>(none)</filename>
    <options>none</options>
    <shade_type>solid</shade_type>
    <pcolor>#4E3E29</pcolor>
    <scolor>#7F7F7F</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Dawn Of Ubuntu</name>
    <filename>/usr/share/backgrounds/Ubuntu-DawnOfUbuntu_1600x1200.png</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#2C160A</pcolor>
    <scolor>#2C160A</scolor>
  </wallpaper>
</wallpapers>


---

### Post by kabronkline on 2006-06-03
Anybody......?

---

