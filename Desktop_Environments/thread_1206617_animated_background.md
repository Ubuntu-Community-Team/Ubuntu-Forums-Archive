---
title: "animated background"
date: 2009-07-07
forum: Desktop Environments
---

### Post by davidjmorin on 2009-07-07
hey everyone. still very new to Linux and Ubuntu.  im looking to get something like the matrix look where it scrolls down....how can i get that effect.  I have compiz installed and got it working last night and i see alot of cool effects you can do. 

anotehr question in relation to compiz...... how can i change the background that shows when in 3d cube mode? also is there a way to have it so that the cube stays without me holding ctrl+alt ? 

thanks everyone for your help

Dave

---

### Post by Idefix82 on 2009-07-07
For an animated wallpaper you can try this: [http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/]("http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/")

The settings for the background image when the cube rotates are in the cube rotate plugin under the Skydome tab.

---

### Post by davidjmorin on 2009-07-07
i cannot find a wrking link to that program at all. do you have any suggestions on where to get it? or maybe another program that will allow that same feature?

---

### Post by overdrank on 2009-07-07
> **davidjmorin said:**
> i cannot find a wrking link to that program at all. do you have any suggestions on where to get it? or maybe another program that will allow that same feature?

You can try [here]("http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap")

---

### Post by Anaxis on 2009-07-07
> **davidjmorin said:**
> 
anotehr question in relation to compiz...... how can i change the background that shows when in 3d cube mode? 
  
This can be done in several ways. If you'd like multiple backgrounds (wallpapers to appear) on the cube faces themselves, there's an option under Compiz's settings called "Wallpaper" that allows you to provide filepaths for different wallpapers. But first, you have to disable Nautilus' drawing of the desktop under gconf-editor->apps->Nautilus->preferences, and uncheck the box that says "show desktop."

If you're referring to the area behind the cube, there are options under Compiz's settings manager that allow you to change the "Skydome," either choosing a colour grandient or uploading your own picture filepath.

---

### Post by davidjmorin on 2009-07-08
hey all....great news.... i got the xwinrap to download and have been playing around with it....first issue was i couldnt get it to work in background but have found the solution for all looking it is as follows
xwinwrap -ni -argb -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID -delay 50000 -no-fog -density 4
  new issue, how do i now change my background color? its that ugly skin color and i cannot figure out how to change it. suggestions?
and also why when i close the terminal does it stop the background from working?

---

### Post by Anaxis on 2009-07-09
The animated background under xwinwrap should continue working even after the terminal is closed, because it is a working program in itself. You're using the terminal simply to edit the configuration of xwinwrap as though it had a graphical program menu, but without the graphical program menu.

As far as changing the color of the interface, simply right click on the desktop (assuming you still have nautlilus drawing the desktop), choose "Change Desktop Background," and on the top left, there's a tab for "Theme."

Under that theme tab, you can customise any of the default themes in quite a few colours and ways to suit your fancy.

Hope that helped!

---

