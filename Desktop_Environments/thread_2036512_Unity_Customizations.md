---
title: "Unity Customizations"
date: 2012-08-02
forum: Desktop Environments
---

### Post by Shadius on 2012-08-02
Hey everybody! :) 

It seems that the Unity Launcher changes colors to match whatever wallpaper is being used. I would like to set it to a specific color and not change according to the wallpaper. I want the Dash button to be either Ubuntu's orange or black. Any color I choose. I've tried using MyUnity to do it, but maybe I'm using it wrong. How can I do this?

---

### Post by 3Miro on 2012-08-02
The Unity panel is simply semi-transparent and it shows the colors behind it. You can adjust that with Ubuntu Tweak tool

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Frogs Hair on 2012-08-02
Changing the dash icon color is a matter of changing the launcher_bfb.png in usr/share/unity/5. I had to locate and change the size/color of an Ubuntu icon I wanted to use with Gimp. The default icon was saved just in case and I then replaced the icon in the location above. Root permissions are needed  to make changes to the file system.

---

### Post by Shadius on 2012-08-02
When using MyUnity, everytime I change the color of the Launcher, the whole thing changes. If it's semi-transparent and shows the color behind it, shouldn't it be showing my webpage background in the screenshot instead of blue? I didn't even set it to blue, it got that way based on my wallpaper. I don't know if I'm making myself clear, but the problem is whenever I change a wallpaper, the Dash and Launcher will match itself to that wallpaper. 

Is Ubuntu Tweak any better than MyUnity? I went to the site and it says it's for 11.04 and before.

---

### Post by Frogs Hair on 2012-08-02
The white Ubuntu logo in the middle of the dash icon can be changed as I described , but the area around it is transparent and shows the color of the wallpaper.

Ubuntu Tweak can be installed on 12.04 via PPA, but only changes the level of transparency/opacity in the launcher and not the color. 

[http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-0-7-0-in-ubuntu-12-04-precise.html](http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-0-7-0-in-ubuntu-12-04-precise.html)

---

### Post by Shadius on 2012-08-02
> **Frogs Hair said:**
> The white Ubuntu logo in the middle of the dash icon can be changed as I described , but the area around it is transparent and shows the color of the wallpaper.

Ubuntu Tweak can be installed on 12.04 via PPA, but only changes the level of transparency/opacity in the launcher and not the color. 

[http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-0-7-0-in-ubuntu-12-04-precise.html](http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-0-7-0-in-ubuntu-12-04-precise.html)

Oh I see. Thank you. I wonder if they'll add any customization options to Unity int eh future versions of Ubuntu..

---

### Post by goonybird on 2012-08-27
Hi.

My question seems to fit this thread...

Changing the Launcher to transparent, which I like, also changes the Dash to solid black. Whatever I do the result is always the same. Either have a coloured semi-transparent Dash OR a transparent Launcher. 

Why can't we have both?

---

### Post by Shadius on 2012-08-27
> **goonybird said:**
> Hi.

My question seems to fit this thread...

Changing the Launcher to transparent, which I like, also changes the Dash to solid black. Whatever I do the result is always the same. Either have a coloured semi-transparent Dash OR a transparent Launcher. 

Why can't we have both?

Agreed.

---

### Post by Frogs Hair on 2012-08-27
Currently the Dash Blur setting can be changed from the CCSM > Unity Plugin > Experimental > Dash Blur. Ubuntu Tweak has the setting as well for Unity 3D. I'm not sure if that is what you are after though.

---

### Post by goonybird on 2012-08-27
Thanks Frogs Hair. That doesn't change the colour though.

My Unity will set the Launcher to clear but the Dash turns black. Changing the Dash colour then un-sets the Launcher transparency.

Ubuntu Tweak will change the Launcher transparency but there is no transparency setting for Dash, only blur.

Need something that has both settings perhaps.

---

### Post by Frogs Hair on 2012-08-27
You can check out the  MyUnity PPA , I have read that the latest version has color adjustments.[http://www.ubuntugeek.com/myunity-3-0-released-and-ppa-installation-instructions-included.html](http://www.ubuntugeek.com/myunity-3-0-released-and-ppa-installation-instructions-included.html)

---

