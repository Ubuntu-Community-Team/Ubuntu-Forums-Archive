---
title: "How do I change my main menu icon?"
date: 2009-01-31
forum: General Help
---

### Post by grndslm on 2009-01-31
I finally found a sweet icon set I liked, [Docang](http://www.gnome-look.org/content/show.php/Docang-Icons?content=70622), but I can't figure out how to change gnome's main menu icon.  I tried editing the value in gconf, but that didn't work.  I tried replacing the icon (originally .png but changed it to .svg thru inkscape), but that didn't work.  I tried following some other directions to delete the icon cache, but that didn't work either.

What else is there for me to do?

---

### Post by vegetarianshrimp on 2009-01-31
It says to do this:

**copy Docang.tar.gz in your ./icons/ or /usr/share/icons**
 
[B]Extract
tar zxvf Docang.tar.gz[/B]


did make sure you copied it into the right place?

---

### Post by Crafty Kisses on 2009-02-01
Here, check out my tutorial: [http://ubuntuforums.org/showthread.php?t=920284&highlight=HOWTO+change+start+icon](http://ubuntuforums.org/showthread.php?t=920284&highlight=HOWTO+change+start+icon).

---

### Post by Oblivion.Wielder on 2009-02-01
You could also change by installing ubuntu tweak, which i personally find easier

---

### Post by grndslm on 2009-02-02
> **vegetarianshrimp said:**
> did make sure you copied it into the right place?I most definitely did that.

Question was how to change a specific icon in that set...

> **Codename said:**
> Here, check out my tutorial: [http://ubuntuforums.org/showthread.php?t=920284&highlight=HOWTO+change+start+icon](http://ubuntuforums.org/showthread.php?t=920284&highlight=HOWTO+change+start+icon).I found some info similar to that before, and it didn't help.  I only changed the distributor-logo.svg icon at first, and it stayed the same main menu icon.  Today, I realized that there are multiple icons in the scalable/places/ directory, like start-here.svg gnome-main-menu.svg xgnome-main-menu.svg and so on.  I replaced all of those with the new ubuntu icon I wanted, but now there's just an empty space to the left of the main menu applet.  So at least it's somewhat working now that I know there's more than just one file to replace.

Perhaps my problem has to do with converting a .PNG to a .SVG ??  I just used inkscape to open the png and save it as a svg file.  I'm hoping that's all I need to do, but it hasn't worked yet.

Also, when I run the gtk-update-icon-cache program... I get one of these 2 errors:

```
root@BlackBox:~# gtk-update-icon-cache /usr/share/icons/Docang/
gtk-update-icon-cache: Failed to open file /usr/share/icons/Docang/.icon-theme.cache : File exists
```

... or if I delete the .icon-theme.cache file, I get... 

```
root@BlackBox:~# gtk-update-icon-cache /usr/share/icons/Docang/
gtk-update-icon-cache: The generated cache was invalid.
```

Can anybody explain the format of these icon directories??  ... and what the gtk-update-icon-cache program is really doing?  Thanks!

---

### Post by OrangeCrate on 2009-02-02
I'm running a custom icon for the start menu, and this is how I do it...

Find a .png logo you want to change it to, and put it in your Home folder labeled:

start-here.png

Then open your terminal, and type the following command:

gconf-editor 

When you execute this command, a configuration editor window will open. Then, go down the list on the left and do the following:

apps > panel > objects > object_0

Your start menu icon will probably be object_0, but it may be another object. Look at them all.

When you find it, then, in the right pane, check the box for Use_Custom_Icon. Then, go up and right click:

custom_icon > Edit Key 

In the value box type:

/home/USERNAME/start-here.png 

Once you have entered this into the box, click OK.

If you followed all steps correctly, then you should see your new icon on your Main Menu.

---

### Post by grndslm on 2009-02-02
> **OrangeCrate said:**
> If you followed all steps correctly, then you should see your new icon on your Main Menu.No, I don't.  I've already done this before.  I did not, however, pick up on the separate check box to "use custom icon".  After selecting that, the problem still persists in that I can't customize the friggin' gnome-main-menu icon.  Are you guys even using Intrepid??

The only other ways I'm varying my menu icon setup is by putting it in /usr/share/icons/ instead of my home folder.  And the name of the icon shouldn't matter right?

I had set /usr/share/icons/orb-big-white.png as a Mandatory key in gconf-editor... and now it won't let me unset the key and change it to /usr/share/icons/start-here.png ... this is all so ridiculously st00pit (and yes, I know all about super user permissions, so that's not the problem).  I'm wondering why I used to like Ubuntu so much with as much crap has been let into Intrepid.

---

### Post by OrangeCrate on 2009-02-02
> **grndslm said:**
> **No, I don't.  I've already done this before.  I did not, however, pick up on the separate check box to "use custom icon".  After selecting that, the problem still persists in that I can't customize the friggin' gnome-main-menu icon.  Are you guys even using Intrepid??**

The only other ways I'm varying my menu icon setup is by putting it in /usr/share/icons/ instead of my home folder.  And the name of the icon shouldn't matter right?

I had set /usr/share/icons/orb-big-white.png as a Mandatory key in gconf-editor... and now it won't let me unset the key and change it to /usr/share/icons/start-here.png ... this is all so ridiculously st00pit (and yes, I know all about super user permissions, so that's not the problem).  **I'm wondering why I used to like Ubuntu so much with as much crap has been let into Intrepid.**

Yes, I'm using Intrepid. Yes, I followed my own advice on how to install a custom icon.

The proof that it works is in the screenshot below. Do you see the icon in the upper left hand corner, and do you see what the configuration file should look like?

Edit:

BTW, we're just a bunch of volunteers. When people here try to help you, watch your mouth, or no one will try to help you again. We're not a paid customer service department, where we'll quietly sit, and listen to you vent on how you're not smarter than your computer.

---

### Post by grndslm on 2009-02-02
I'm not complaining to those who are helping me... I'm complaining to those who are letting this stuff get released.  There's supposed to be circular feedback somewhere in the loop, no?  Last time I checked, I was easily able to customize certain things in an Ubuntu install... now usplash is extremely difficult to change from default, and I can't change the main menu icon with 2 different ways that both should definitely work, and there's a ridiculously crazy bug with Xorg on my laptop.  Many steps forward, but many more steps back for me.

Anyway... to answer your question, yes... I my gconf-editor looks just like that for the main-menu object.  Mine just says "menu_bar_screen0" instead and the icon is point to /usr/share/icons/start-here.png instead of a start-here.png in my home directory... and yes the start-here.png is chmod 755.  It should work.  I've run gconf-editor as SU to make that object's settings mandatory, and then I changed it to just be default, and I've changed it in my own personal user's gconf-editor.  It works neither way, hitting killall gnome-panels after every change to see which one makes a difference.  It's just the default Human start-here icon now that I've switched back to that theme.

---

### Post by grndslm on 2009-02-02
> **OrangeCrate said:**
> Yes, I'm using Intrepid. Yes, I followed my own advice on how to install a custom icon.Just sounded odd because two fresh Intrepid installs shouldn't have so many differences between them.  I have differences between my desktop and laptop, and your object in gconf also looked different from my 2 installs.  Very weird stuff.

> **OrangeCrate said:**
> The proof that it works is in the screenshot below. Do you see the icon in the upper left hand corner, and do you see what the configuration file should look like?My proof is in that my gconf looks similar enough, but it still doesn't show anything different from Human's default ubuntu main-menu icon.

> **OrangeCrate said:**
> BTW, we're just a bunch of volunteers. When people here try to help you, watch your mouth, or no one will try to help you again. We're not a paid customer service department, where we'll quietly sit, and listen to you vent on how you're not smarter than your computer.I'm smarter than the computer, but again... this software is buggy.

---

