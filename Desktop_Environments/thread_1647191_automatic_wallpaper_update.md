---
title: "automatic wallpaper update"
date: 2010-12-16
forum: Desktop Environments
---

### Post by shawn.abdushakur on 2010-12-16
Hi all,

I have Ubuntu Lucid and am wondering how to have the wallpapers in the Background tab of the Appearances dialog box update automatically when I add a wallpaper to /usr/share/backgrounds. Or should I be putting them somewhere else for this to happen? I have several accounts on my computer and can't go into each account and manually update whenever I add a wallpaper.

Thanks in advance.

Shawn

---

### Post by Krytarik on 2010-12-17
I've also searched for a way to do this just yet, unfortunately unsuccessful. But I've found the file in which the background-image information is stored: ~/.gnome2/backgrounds.xml. You could use a shared location for this file, with appropriate permissions of course, and symlink it to the various user profiles. This way you have at least only to add the new backgrounds to the choice-window one time.

Greetings

---

### Post by shawn.abdushakur on 2010-12-19
Well, here are the contents of my backgrounds.xml:

<?xml version="1.0"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers/>

Unfortunately, that's not gonna help me. Thanks for the info though.

---

### Post by Krytarik on 2010-12-21
> **shawn.abdushakur said:**
> Well, here are the contents of my backgrounds.xml:

<?xml version="1.0"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers/>

Unfortunately, that's not gonna help me. Thanks for the info though.
This cannot be the case if you have backgrounds in the selection window of the current user and you are using the standard gnome-desktop (?).

These are the default backgrounds:
```
<?xml version="1.0"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers>
  <wallpaper deleted="false">
    <name>Fluffodome</name>
    <filename>/usr/share/backgrounds/Fluffodome.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#01011b1b3636</pcolor>
    <scolor>#01011b1b3636</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Curls by Candy</name>
    <filename>/usr/share/backgrounds/CurlsbyCandy.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#a0a09b9b9090</pcolor>
    <scolor>#a0a09b9b9090</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>In the dark Redux</name>
    <filename>/usr/share/backgrounds/InthedarkRedux.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#000000000000</pcolor>
    <scolor>#000000000000</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Out of focus</name>
    <filename>/usr/share/backgrounds/Outoffocus.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#c9c93d3d4545</pcolor>
    <scolor>#c9c93d3d4545</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>SmoothMoment</name>
    <filename>/usr/share/backgrounds/SmoothMoment.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#babababababa</pcolor>
    <scolor>#babababababa</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Kein Arbeitsfl&#xE4;chen-Hintergrund</name>
    <filename>(none)</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#000000000000</pcolor>
    <scolor>#2c2c00001e1e</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Weltraum</name>
    <filename>/usr/share/backgrounds/cosmos/background-1.xml</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#000000000000</pcolor>
    <scolor>#2c2c00001e1e</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Busqueda Nocturna</name>
    <filename>/usr/share/backgrounds/BusquedaNocturna.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#000000000000</pcolor>
    <scolor>#000000000000</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Daisy</name>
    <filename>/usr/share/backgrounds/Daisy.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#00005555ffff</pcolor>
    <scolor>#00005555ffff</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Cornered</name>
    <filename>/usr/share/backgrounds/Cornered.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#212127270303</pcolor>
    <scolor>#212127270303</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Fall Drops, Ancient Light</name>
    <filename>/usr/share/backgrounds/FallDrops,AncientLight.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#000000000000</pcolor>
    <scolor>#000000000000</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Icy stones 2</name>
    <filename>/usr/share/backgrounds/Icystones2.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#717172728585</pcolor>
    <scolor>#717172728585</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Pointy</name>
    <filename>/usr/share/backgrounds/Pointy.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#646467676a6a</pcolor>
    <scolor>#646467676a6a</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Ubuntu</name>
    <filename>/usr/share/backgrounds/warty-final-ubuntu.png</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#2c2c00001e1e</pcolor>
    <scolor>#2c2c00001e1e</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Warmlights</name>
    <filename>/usr/share/backgrounds/Warmlights.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#373720200f0f</pcolor>
    <scolor>#373720200f0f</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Yellowflower</name>
    <filename>/usr/share/backgrounds/Yellowflower.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#9393a6a6b5b5</pcolor>
    <scolor>#9393a6a6b5b5</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Bosque TK</name>
    <filename>/usr/share/backgrounds/BosqueTK.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#000000000000</pcolor>
    <scolor>#000000000000</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Maraetai before sunrise</name>
    <filename>/usr/share/backgrounds/Maraetaibeforesunrise.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#09091d1d5c5c</pcolor>
    <scolor>#09091d1d5c5c</scolor>
  </wallpaper>
</wallpapers>
```

---

