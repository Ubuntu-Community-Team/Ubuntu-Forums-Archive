---
title: "How do I create a boot splash theme from a collection of photos and videos?"
date: 2014-03-04
forum: Desktop Environments
---

### Post by ved2254 on 2014-03-04
I want to customize Ubuntu with a personal touch. Instead of other wallpaper substitutes, I would like an animated boot splash image with my photos. I had a look at Ubuntu sunrise. Is there any way I can get a theme which works similar to this but with my photo stream?

Theme in action:
[http://www.youtube.com/watch?v=sqc55gPDRss](http://www.youtube.com/watch?v=sqc55gPDRss)

Source:
[http://gnome-look.org/content/show.php/?content=129696](http://gnome-look.org/content/show.php/?content=129696)

---

### Post by deadflowr on 2014-03-04
I'm thinking you should look at the package
plymouth-theme-script

It's in the repos.(software center/synaptic)

---

### Post by Portaro on 2014-03-05
Yes you can use a custom script but many photos I think this is not possible PLaymouth uses one background and one logo or text logo.

Maybe you can use some gif file (but I unknow if Plymouth supports .gif type file) or make a background with your Photos like a land panorama or else in Gimp and then puth this background (be sure that background have a reasonable properties image size) and put on the /lib/plymouth/themes/name_of_your_theme.

update grub
and 
update  initramfs

---

### Post by grahammechanical on 2014-03-06
You could install what you are seeing in that video, see how good it runs and then track down the location of its scripts and images and see if modifying the scripts to point to your images works. But be prepared to break your system. Install another version of Ubuntu in another partition and experiment with that.

Regards.

---

### Post by ved2254 on 2014-03-18
I got a general guide at the [official page]("http://www.freedesktop.org/wiki/Software/Plymouth/Scripts/") and [COLOR=#000000]this site : [/COLOR][http://brej.org/blog/?cat=16]("http://%26quot%3Bhttp//[/url")[COLOR=#000000].[/COLOR][COLOR=#000000] However, to test the themes, I need to install them and then emulate them. How can I emulate them without installing them so as not to (possibly) damage my system?[/COLOR]

---

