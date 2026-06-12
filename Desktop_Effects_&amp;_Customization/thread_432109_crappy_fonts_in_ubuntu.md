---
title: "crappy fonts in ubuntu"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by fadetoblack82 on 2007-05-03
im trying to get decent looking fonts and was told to install the msttcorefonts package.. but when i do that this happens:

```

ar@r60:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

```

---

### Post by kelvin spratt on 2007-05-03
yet another one i used windows before this is crap then go back or ask politely if there are some better fonts
this free not hundreds of dollars and its good points far out way its bad points

---

### Post by Medieval_Creations on 2007-05-03
There is an easy way to install new TTF fonts into Ubuntu.

1st.) In Windows, copy all the fonts from your fonts folder to a CD or flash drive, if needed.  You could also just mount you windows partition too, depending on your setup.

2nd.) Have the folder open containing all your Windows fonts.

3rd.) Hit "CTRL - L".  It should open a little window asking for the location you want to open.

4th.) Type "fonts:///" (without the quotes) and hit enter.  It should open a window with all the current fonts installed in Ubuntu.

5th.) Select all the fonts from your Windows folder and do a copy/paste into the Ubuntu Fonts folder.

It will give you a status bar on it's progress while copying and then it will disappear as one would expect. Now the fonts have been copied over even though they do not show up, **YET**.

Now reboot and all your fonts should be there.

***Note:***  I'm writing this from memory.  I'm not at home at the moment.  I will check the steps again when I get home to make sure they are accurate.

---

### Post by NilsE on 2007-05-03
Go into System/Administration/Software Sources and turn on Multiverse (4th one dfown) then try again. Youi will also be able to do it from Synaptic but you may have to reload repository first.

---

### Post by reclusivemonkey on 2007-05-03
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty)

---

### Post by LuisGMarine on 2007-05-03
The guide above has a lot of good information, it is what I followed to get some sleek fonts.  I also have this config, I don't know how much it will help, but I guess to some people its making a lot of difference.

=================================

Type this into terminal:
```
gedit ~/.fonts.conf
```

Then, copy and paste this code into it:
```
<?xml version='1.0' ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target='font'>
<edit name='autohint' mode='assign'>
<bool>true</bool>
</edit>
</match>
</fontconfig>
```

Hit 'Save', and restart X or reboot, just to make sure everything loads perfectly.  

================================

Someone claimed that the code above didn't work, but once they removed this part from the code, it worked perfectly.
```
<?xml version='1.0' ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig> 
```

[Here is the thread]("http://ubuntuforums.org/showthread.php?t=425579")

Good Luck!

---

### Post by fadetoblack82 on 2007-05-04
> **kelvin spratt said:**
> yet another one i used windows before this is crap then go back or ask politely if there are some better fonts
this free not hundreds of dollars and its good points far out way its bad points

what??? i have no idea what you are saying

thanks for all the help, the fonts are looking much better now..i followed Medieval_Creations instructions and that worked great

---

### Post by Medieval_Creations on 2007-05-05
Glad it worked for you.

---

