---
title: "Small window edges, hard to resize"
date: 2009-07-23
forum: Desktop Environments
---

### Post by bunorama on 2009-07-23
Resizing windows is way too difficult because the edge is too small. 
I read that you can hold down alt to resize, I don't want that, I want bigger edges.

I read a bug thread about this that went on for years, seems devs are not interested in enhancing this aspect of the desktop environment.   It said that metacity, is that true?  What can I replace metacity with?

---

### Post by Patricrawley on 2009-07-23
Ubuntu comes with compiz pre-installed on it and there is another window decorator that comes partnered with compiz called emerald. Install compizconfig-settings-manager, fusion-icon, and emerald.
```

sudo apt-get install compizconfig-settings-manager fusion-icon emerald

```
The go to Applications>System Tools>Compiz Fusion Icon. There will now be a blue box icon in your system tray, right click on this and click on Emerald Theme Manager. By default it will not have anything installed in it, but you can find some themes [here]("http://gnome-look.org/index.php?xcontentmode=103") under Beryl on gnome-look.org. Download a file and import it in the Emerald Theme Manager or create one, it's your choice. Then when you have a theme installed, click on that theme and exit the program. Go back to the Compiz Fusion Icon in your tray and Select Window Manager and select Emerald. If the window borders are too small, reopen the Emerald Theme Manager. Go the the Edit Themes tab, then select the Frame/Shadows sub-tab. The right hand side of this pane allows you to manipulate the size of your window borders, then it is up to you to find a size appropriate for your needs. I hope this helps.

---

### Post by bunorama on 2009-07-23
Thanks, that works, and helps a lot.  
I've been kinda afraid to install things, after reloading a few times now.

I noticed that in full screen, the window cannot be resized, which is good, but the resize arrow shows. I guess it's a bug.

Emerald themes are really cool :)

---

### Post by mixmastamyk on 2011-05-03
I was facing the same issue, found this (less invasive way) to work:

```
sudo nano  /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml 

```

And edit the attributes below:
```

<!-- General window layout -->
<frame_geometry name="frame_geometry_normal" title_scale="medium" rounded_top_left="true" rounded_top_right="true"  rounded_bottom_left="false" rounded_bottom_right="false">
 	<distance name="left_width" value="3"/>
	<distance name="right_width" value="3"/>
	<distance name="bottom_height" value="3"/>


```

3 seemed to work well for my hi res laptop screen, 5 was a bit too much.

---

