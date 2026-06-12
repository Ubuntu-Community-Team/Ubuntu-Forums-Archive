---
title: "Change the input boxes background color"
date: 2012-02-29
forum: Desktop Environments
---

### Post by sfang on 2012-02-29
Hello,

I've recently installed Xubuntu 11.10 and it's working fine. However, I'd like to know how I can change the background color for all input windows as it's too white for me. I want to change its value to something easier on the eyes.

There is a way to do it through the GUI on the old Ubuntu+Gnome 2 combo (Preferences > Appearance > Customize Theme > Colors > Input boxes), but I can't find anything similar with Xfce.

Thanks.

---

### Post by Toz on 2012-02-29
Hello and welcome to the forums.

Unfortunately, this ease of configuration doesn't exist in xfce as it does in gnome. 

The easy way is to choose another appearance theme (Settings -> Settings Manager -> Appearance -> Style tab).

The harder way is to directly manipulate the gtk-2.0/gtkrc or gtk-3.0/* files for the theme in the configuration files located in /usr/share/themes/<theme>. (In which case, it would be best to make the changes locally in ~/.gtkrc-2.0 or ~/.config/gtk-3.0/settings.ini). 

Have a look at the existing config files in /usr/share/themes for examples.

Here is another reference thread: [http://ubuntuforums.org/showthread.php?t=377397&highlight=gtkrc+tutorial]("http://ubuntuforums.org/showthread.php?t=377397&highlight=gtkrc+tutorial").

---

### Post by sfang on 2012-02-29
I managed to change the color. Thank you, Toz! :D

If anyone is interested, here is how I did it: 

1. Choose the color you want and find its hex value (eg. #FFFFFF = white)
 1. Choose the theme you want to use 
 2. Go to* /usr/share/themes* and copy the folder of theme you chose 
 3. Go to */home/~/themes* and put the folder you've just copied there (if *themes *doesn't exist, create it) 
 4. Open the *gtkrc* file in Leafpad (or any other text editor) and look for *base_color* (or *nbase_color*) in the *gtk-color-scheme* line.  The syntax varies according to the theme.
 5. Put the hex value of the color you want and save.  (eg. *nbase_color: #FFFFFF*)
 
After that, any window you open (Firefox, Leafpad, Tunar) will have the new input background color.  Seems like the local *themes* (*/home/~/themes*) overrides the global one (*/usr/share/themes*), so all you have to do is select the theme you changed in the *Configuration Manager > Appearance* window.

Note that the changes will be limited to your own account &#8211; if you create a new user account, the new settings won't be carried over. You can edit the *gtkrc* file in */usr/share/themes* in order to apply the changes globally. Keep in mind you'll need elevated rights to do so.

Again, thank you very much!  
 
Ps: ~ = your account's name
PPs: Tested with gtk-2.0 themes.

---

