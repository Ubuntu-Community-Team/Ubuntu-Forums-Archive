---
title: "Ok, I give up. I need help on Beryl"
date: 2007-05-29
forum: Desktop Effects &amp; Customization
---

### Post by xMAVERICKx01 on 2007-05-29
I have tried just about EVERY guide for installing Beryl. I'v gotten it installed but when i try to activate the Beryl Window Manager it flashes all the windows and goes back the the Metacity one. I have emerald themes installed and what not but I cant seem to get it to work! I'm a noob at this linux thing and I know i should probably learn to use linux better but I dont want to have to wait a couple years to get Beryl working. PLEASE HELP! all help would b greatly appreciated :D thanks!

---

### Post by starcraft.man on 2007-05-29
> **xMAVERICKx01 said:**
> I have tried just about EVERY guide for installing Beryl. I'v gotten it installed but when i try to activate the Beryl Window Manager it flashes all the windows and goes back the the Metacity one. I have emerald themes installed and what not but I cant seem to get it to work! I'm a noob at this linux thing and I know i should probably learn to use linux better but I dont want to have to wait a couple years to get Beryl working. PLEASE HELP! all help would b greatly appreciated :D thanks!

Your on an ATI card, you installed the graphics driver first? Thats really the only hard part, then you just follow [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29") I believe. Getting Beryl to work on Feisty is harder with the ATI card, try to follow it closely. I am also pretty sure you want to follow the second (closed source) guide.

I don't know the particular problem your having, it could be any number of things... likely some manual settings need to be changed to get it working. Follow the steps and take it nice and slow. Good luck. :)

---

### Post by bone43 on 2007-05-29
> **starcraft.man said:**
> Your on an ATI card, you installed the graphics driver first? Thats really the only hard part, then you just follow [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29") I believe. Getting Beryl to work on Feisty is harder with the ATI card, try to follow it closely. I am also pretty sure you want to follow the second (closed source) guide.

I don't know the particular problem your having, it could be any number of things... likely some manual settings need to be changed to get it working. Follow the steps and take it nice and slow. Good luck. :)


Yes this guide works with the close source version i used it just recently and i am typing this with berly running on a ATI x1400, make sure you are running XGL you should be loging into a ghome-xgl session from the log in screen.

---

### Post by Vorian on 2007-05-29
*moved to desktop effects*

---

### Post by Kuoi on 2007-05-29
Some suggestions from me, because I use Beryl only a few days and learned already a lot

Rightclick on the Beryl Icon , and select "Beryl Settings Manager" .

Click above on "General Options" and make sure to have the following options :

Horizontal Virtual Size : 4
Vertical Virtual Size : 1
Number of desktops : 1

Now close the window and rightclick on the Beryl Icon again , ... now select "Advanced Beryl Options" > "Rendering Path":
Set this to 'Copy'

These settings seems to be important , as far as I can remember and as far as I've configured Beryl so far.
---------------------- Try this too if it isn't working yet :
Try this :

Rightclick on the Beryl Icon , and select "Beryl Settings Manager" 
On top , click on "visual effects" ... now at the left select "Window Decoration"

For this my settings are the following :
At the right click on "Misc. Options" > "Appearance"
'Apply Transparancy/Brightness/Saturation' : that one is selected .
Now click on  "main" , and there you select "Mipmap" ( it's the only setting there ) 

-----------
If it's still not working , do the following :

Type in terminal > gksudo gedit /etc/X11/xorg.conf
Ad this to the section "screen" > Option         "AddARGBGLXVisuals" "True" so it looks like this ... but remember this is mine , yours will be a bit different > Section "Screen"
    Identifier     "Default Screen"
    Device         "Nvidia Geforce 4"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"

And now ad this line at the very end of the file ... > Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Hope this helps , Kuoi

---

