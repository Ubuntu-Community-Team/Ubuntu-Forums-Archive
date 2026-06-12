---
title: "installing various themes"
date: 2005-03-10
forum: Desktop Environments
---

### Post by jhands on 2005-03-10
hi 

 i want to know how to install themes in ubuntu hoary. first of all I want to know what types of themes like gtk 2.0 or gtk 1.0, metacity etc ones can be installed on ubuntu. i was looking in gnome-look.org and i found some nice ones under gtk 2.0.

second how do i install icon themes?

third how do i install splash screens?

and last how do i install cursor themes?

any help would be greatly appreciated

---

### Post by jsgotangco on 2005-03-10
icon sets are installed in ~/.icons folder.

theme sets are installed in ~/.themes folder.

splash screens can be configured in Login Screen Setup or Config Editor.

---

### Post by J. S. Jackson on 2005-03-11
You want "GTK 2.x", "Metacity" and "Icon" themes.  That is how they are listed on GNOME-Look.org.

If you open your theme preferences in Ubuntu/Gnome, and then on the right side list of buttons click "Theme Details" it will, of course, open up a window that has three tabs:

**Controls** - This is what the GTK 2.x themes will change.  Any GTK themes you add will be listed here.
**Window Border** - This is what the Metacity themes will change.  Any Metacity themes you add will be listed under this tab.
**Icons** - Obviously, Icon themes will be listed here.

Some themes you find on GNOME-Look will contain both a GTK, and a Metacity theme.

Probably the easiest way to install these is to open the "Theme Details", as decribed above, and simply drag/drop the package you downloaded right onto the Theme Details window.  No need to decompress it or anything, just drag/drop the file you downloaded right onto that window.  Gnome will pop up a dialog confirming that you wish to install the theme.  GTK 2.x, Metacity, and Icon themes can all be installed this way.

Alternatively, you can do as jsgotangco described in the post above, and simply unpackage the file you downloaded into the appropriate folder, manually.  GTK and Metacity themes go in the .themes folder, Icons go in the .icons folder.

**GDM Themes** - These are the themes for your login screen.  You will find the options to change this theme by opening the System>Administration>Login Screen Setup dialog, then clicking on the "Graphical Greeter" tab.  Click the button at the bottom "Install new theme" and browse to the file you downloaded, etc.

**Splash Screens** - Slightly more complicated. Look [here](http://ubuntuforums.org/showthread.php?t=11478)

Hope that helps.

---

### Post by jhands on 2005-03-11
Great, thank you som much. i just had one last question. How do i install teh mouse themes?

---

### Post by norwyn on 2005-03-15
Hi. I to wants to install themes, though I use Warty. However, I've done as you have written, but I still cannot manage to get it to work. I am pretty new to linux and gnome. When I put the different folders in .icons and .theme they do't show up in the "Themes settings". Also when i install the whole theme using the "Theme settings" nothing happens.  Thanks for your time!

---

### Post by theChauvinist on 2005-03-15
Yes, I want to install a new cursor theme too, but don't know how.

After upgrading to Hoary, I love everything about it except the black cursor that looks like one I hated on Windows, let alone on something as beautiful as Ubuntu. I've found a set I like on gnome-look.org, but don't know what to do with them....?

---

### Post by J. S. Jackson on 2005-03-16
[QUOTE=norwyn]Hi. I to wants to install themes, though I use Warty. However, I've done as you have written, but I still cannot manage to get it to work. I am pretty new to linux and gnome. When I put the different folders in .icons and .theme they do't show up in the "Themes settings". Also when i install the whole theme using the "Theme settings" nothing happens.  Thanks for your time![/QUOTE]

I haven't used Warty in some time, so I don't remember if there is some significant difference.  However, I can tell you that many themes will not add an entry in the main theme window.  You will only see them listed under the appropriate tab under theme details.

If you are installing the theme by using the drag/drop method, or the install theme button, you should not unpack it first.  But if you are installing it manually, into the .theme or .icon folder, you will need to unpack the folders/files first.

I have found several themes on gnome-look that simply do not work correctly.  Perhaps they have been packaged incorrectly by the author, or some other mistake on his part.  Try a couple different themes to be sure that it's not just the theme itself that is at fault?

In regard to mouse themes - I don't really use them, so I'm not sure of the various methods to install them, but I do know that many people use "gcursor".  I installed it on Hoary just to get back to the normal Ubuntu mouse theme.  It can be found in the repositories.

I don't remember if it's in Universe or Multiverse, and also my spelling might be incorrect (I can't check right now, I'm at work, on Windows XP), but I'm sure you'll find it if you have enabled Universe and Multiverse, and search for it in Synaptic.

---

### Post by theChauvinist on 2005-03-16
Thanks, installed gcursor from the universe repository, works like a dream.

---

### Post by unkwn on 2005-03-16
[QUOTE=theChauvinist]Thanks, installed gcursor from the universe repository, works like a dream.[/QUOTE]
 gcursor is nice, but it'd be better if you didn't have to log out and restart gdm for it to take effect.

---

### Post by norwyn on 2005-03-17
Thank you! It was the themes that was packed in a strange way, and therefore didn´t work. Btw, has anyone got Clearlooks to function? Thanks again S.Jackson!

---

### Post by J. S. Jackson on 2005-03-17
[QUOTE=norwyn]Thank you! It was the themes that was packed in a strange way, and therefore didn´t work. Btw, has anyone got Clearlooks to function? Thanks again S.Jackson![/QUOTE]

You're welcome!

Clearlooks is also in the repositories.  I think it has been moved to main?  Well, regardless, do a search for it in Synaptic, and you'll find it.  Make sure you've got Universe enabled and all.

Ah, I just looked back through the thread and see you're using Warty.  I don't know if it's in Warty repositories, but it's definately in Hoary.  In fact the default Human theme is using Clearlooks engine now, in Hoary.

---

