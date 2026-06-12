---
title: "Desktop background bug"
date: 2007-06-03
forum: Desktop Effects &amp; Customization
---

### Post by Geekkit on 2007-06-03
Just in case anyone comes across this problem ...

I've encountered a bug where if you choose System->Preferences->Desktop Background which of course opens up the applet. The applet is happy to comply with a new desktop background (say you grab something from Flickr or something). But when you reboot the image you choose is gone - or at least the choice in the applet (although the image still exists within the file system). To force edit you must go to:

/usr/share/gnome-background-properties

and fire up gedit:

sudo gedit [FONT="Courier New"]ubuntu-wallpapers.xml[/FONT]

(of course offer your password). This will fire up Gedit and open up the  [FONT="Courier New"]ubuntu-wallpapers.xml[/FONT] file for editing. Each entry starts with:

  <wallpaper>
    <name>Simple Ubuntu</name>
    <filename>/usr/share/backgrounds/warty-final-ubuntu.png</filename>
    <options>zoom</options>
    <pcolor>#dab082</pcolor>
    <scolor>#dab082</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
  <wallpaper>

You can change the file path and name (and p and s colors although the p and s colors don't really affect your image - just the theme). That way the next time you reboot the xml file still shows the image backgrounds and thus when you go back to System->Preferences->Desktop Background under the menu, you will still see your background choices.

Hope this helps

;)

---

### Post by bharadwaj on 2008-04-13
Thanx for a really helpfull post bro!
But I just hope that I don't come across this problem :)

---

