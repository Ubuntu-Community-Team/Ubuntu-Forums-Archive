---
title: "Ubuntu Unity GTK, Icon and Window themes cannot be changed"
date: 2015-01-08
forum: Desktop Environments
---

### Post by Vesnog on 2015-01-08
[COLOR=#333333][FONT=UbuntuRegular]I have Ubuntu 14.04.1 LTS 64-bit installed on two separate laptops (**Dell XPS L502X** and **Dell Latitude E5440**). I installed the themes on Dell XPS L502X either by extracting compressed files or using the [/FONT][/COLOR]apt-get[COLOR=#333333][FONT=UbuntuRegular] package manager, so far this procedure worked flawlessly after a fresh install of the OS on Dell XPS L502X; however this is not the case on Dell Latitude E5440 after copying the theme files from XPS to Latitute with an USB stick. What may be the reason behind it?

[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]In order to copy the themes and icons from **XPS** to **Latitude** I used a memory stick and copied the contents of */usr/share/icons* and */usr/share/themes* directories from **XPS** PC which had the themes and icons installed. Later I plugged the flash drive into the Latitude and tried changing themes. In order to be able to set the themes easily I installed **Ubuntu Tweak **from the suggested PPA and I noticed that when I first launched Ubuntu Tweak it failed to show the themes apart from the cursor ones. The **GTK themes **were not shown for example, I thought this might have something to do with file permissions or something so I decided to find which themes can be installed from the repository and installed them accordingly. After this step **GTK** and **icon themes** showed up in the **Ubuntu Tweak Tool**, but when changed into a theme which was not supplied with Vanilla Ubuntu I noticed that there were inconsistencies in color etc. and the theme just did not display properly and for the icon theme not all icons were changes as was the case with XPS. I think I made a blunder here but could not figure out how to remedy it? Any assistance suggestion would be nice.

[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]P.S : The cursor themes work fine, there are no problems with them.[/FONT][/COLOR]

---

### Post by Vesnog on 2015-01-08
I checked and confirmed that the **permissions** are the same on both computers and related **dconf **settings under org -> gnome -> desktop -> interface is the same if I did not miss something. What else should I look at is there any symlinks or anything like update-alternatives involved? I tried altering the theme via bash command prompt too but it did not work either. How can I determine which packages I should have installed in order for a theme to work properly? Furthermore, I noticed that by mistake I copied themes which are installed via a **PPA **is this the reason why it messed up so much? When installed via **PPA **where are the theme files stored and how can Ubuntu Tweak retain the theme names even after I deleted the corresponding files on a system which only had the files copied into it(does not even have the PPAs in its sources)?

EDIT: The themes were in the **/usr/share/themes **directory when I deleted the **UTT **also forgot about them. However I still wonder how themes installed via **PPAs **do they use symbolic links and install the files elsewhere?

---

### Post by Dennis N on 2015-01-08
A couple of comments:

Themes won't work well in Ubuntu unless they have unity support - that is they have a unity folder. Here are two examples. Both are GTK themes, and both support GTK 2 and 3. Greybird should work on Ubuntu since it has a unity folder. Albatross won't work (or works poorly) on Ubuntu since it does not have a unity folder. They both work in Xubuntu, however. In my experience, themes that won't work are not offered as a choice. Could be some exceptions to that observation.


```
dmn@Sydney:/usr/share/themes/Greybird$ ls
gtk-2.0  gtk-3.0  metacity-1  unity  xfce-notify-4.0  xfwm4

dmn@Sydney:/usr/share/themes/Albatross$ ls
gtk-2.0  gtk-3.0  metacity-1  xfwm4


```update-alternatives only deals with two kinds of themes - Plymouth themes and cursor themes:

```
dmn@Sydney:~$ update-alternatives --get-selections | grep theme
default.plymouth               auto     /lib/plymouth/themes/xubuntu-logo/xubuntu-logo.plymouth
text.plymouth                  auto     /lib/plymouth/themes/xubuntu-text/xubuntu-text.plymouth
x-cursor-theme                 manual   /usr/share/icons/FlatbedCursors.Orange.Large/cursor.theme

```

From what I have seen, PPAs offering themes install the folders in a standard location.

---

### Post by Dennis N on 2015-01-08
I earlier put a comment about galternatives on your other thread, in case you missed it:

[http://ubuntuforums.org/showthread.php?t=2259250&p=13203491#post13203491](http://ubuntuforums.org/showthread.php?t=2259250&p=13203491#post13203491)

---

### Post by Frogs Hair on 2015-01-08
If any themes copied to USB  from usr/share/themes have a PPA as their origin I would delete them for two reasons . one they won't update and two , if you enable the PPA source on the second machine  you may end up with package system problems.

---

### Post by Vesnog on 2015-01-11
> **Frogs Hair said:**
> If any themes copied to USB  from usr/share/themes have a PPA as their origin I would delete them for two reasons . one they won't update and two , if you enable the PPA source on the second machine  you may end up with package system problems.

I deleted and re-installed them via adding the PPAs or manually downloading them, now everything works flawlessly. Thanks for your support.

---

