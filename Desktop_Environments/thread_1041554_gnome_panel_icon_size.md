---
title: "gnome panel icon size"
date: 2009-01-16
forum: Desktop Environments
---

### Post by madmax1735 on 2009-01-16
on ubuntu intrepid i have been reduce the size of my panel in order to get a cleaner look.

theme:glossy, icon:mist

for top panel reducing font size enables you to set panel size to 19 but the icons stay size 24.

to change icon size in configuration editor i set key:

/desktop/gnome/interface/toolbar_icons_size = small-toolbar

but the icon size still doesnt change and prevents panel from becoming smaller. you can set the bottom panel to size 19, it works but the icons get cut from both top and bottom

at boot though icon appear in size 19 for a second or two but then change bk to size 24.

can someone help. a workaround mayb.

earlier i was using mac4lin on intrepid and was successfully able to set the panel size to 19. but i dont wanna install it this time and wanna stick to ubuntu default themes.

---

### Post by gettinoriginal on 2009-01-16
gnome-color-chooser (in Synaptic) allows for font change of size and font. :P

---

### Post by madmax1735 on 2009-01-16
hey i have no clue about how to use the gnome color chooser to reduce the size of icons on the panel........



wht do i change...........i have already played around with the settings..... it doesnt seem to work....

lill help.....

---

### Post by madmax1735 on 2009-01-16
okey a work around...


it seems that the ubuntu menu is holding the panel and other icons to size 24.

if u do remove ubuntu menu.
the panel shrinks down to the specified size.....


i have put the main menu instead of ubuntu menu....

can any one help me put the places and system menu back into the panel, as in its all under one singel menu like xp or something. i dont like that :(

---

### Post by madmax1735 on 2009-01-17
lill help???

---

### Post by gettinoriginal on 2009-01-17
gnome color chooser, select icons, tic the box of the item you want to change, and change the size. Note: some gtk-2 themes have their own settings and won't allow changes, so just find a theme you like that will.  My panel properties show 24 pix, and is normal for me, but maybe I am not understanding what you are trying to do ??

---

### Post by madmax1735 on 2009-01-17
aim: to get a smaller panel (size 20) which retains the functionality of the original ubuntu panel (like launcher for "places" & "system" with custom menu and also looks the same.

problem: ubuntu custom menu has a bug which prevents icons in the panel from becoming small even if u set the size to 20 and the icons stay size 24 eventhough they are supposed to be scalable.

i have attached screenshots for clarity. 

"without.the.custom.menu" shows till where i have managed to reached. now i want to add the "places" and the "system" launchers to the panel also. like in the custom menu. as seen in "with.custom.menu"

---

### Post by madmax1735 on 2009-01-17
humm nobody seems to have a clue abt wht i am tryin to do....

:(


help!

---

### Post by Fabje on 2009-02-13
I've got the same problem here.
Anyone got the solution for this?


Edit:
Found a solution!
Well, its more of a hack.

I dont know why, but it seems that the "costum menu bar" doesnt scale its icon but just grabs the 24px icon.
The hack to this is to replace the file of the 24px icon to the size you like.
The file is located here: /usr/share/icons/gnome/24x24/places/start-here.png

I reccomend you rename it to /usr/share/icons/gnome/24x24/places/start-here.png.bak

Now you can copy a file from the desired size to the folder for example from: /usr/share/icons/gnome/**16x16**/places/start-here.png

Log out, and log in again.
Now you have your very own nice and small panel.

---

### Post by madmax1735 on 2009-02-15
thanks a lot, it worked...

---

### Post by namaku0 on 2009-05-04
How about this:
Open **gconf-editor**, go to **/desktop/gnome/interface**,
untick the **menus_have_icons**.

EDIT: Forget it, it disable icons on many places too.

---

### Post by madmax1735 on 2009-08-10
hey, sorry i am posting in this thread after a long time.


on how to change size on icons in the top panel while using the default Ubuntu start menu in gnome please refer to this launchpad bug

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/223075](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/223075)

solution by paul boyle :
-------------------------------------------------------------------------
This hack is for the desperate and the curious. It will be overwritten by theme upgrades and pays no heed to security concerns. If you don't understand what the following commands do then PLEASE don't execute them. You should always know how to undo changes YOU make to YOUR system.

I sledgehammered a dirty fix by backing up then soft linking all relevant "icon size" directories to the 16x16 counterpart. e.g. using icon set Gion (these settings trickle through a hierarchy specific to your setup - this is for guidance only!!):

cd /usr/share/icons/Gion
sudo mv 24x24 24x24_bak
sudo ln -s 16x16 24x24

Repeat for any size/icon that you think might be relevant (including 'scalable'). Reboot X.
------------------------------------------------------------------------

with the method posted here, size of icon in the top panel of gnome can be reduced, but it wont reduce the size of icons in the drop down menu.

to change the size of the icons in the drop down menu in gnome, use the gnome-color-chooser 

select > icon tab >  set the icon size to desired > log out and log in to gnome for changes to take effect

---

### Post by tryguy on 2009-10-25
I reduced gnome icon sizes without any hassles. Just follow 3 simple steps.

1. Install gnome color chooser and open it from Preferences menu
2. From the icons tab, select desired sizes
3. Reboot

Settings won't work with Human theme or Redmond

---

