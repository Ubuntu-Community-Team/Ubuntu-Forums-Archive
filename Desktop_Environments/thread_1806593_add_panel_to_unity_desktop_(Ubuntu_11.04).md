---
title: "add panel to unity desktop (Ubuntu 11.04)"
date: 2011-07-17
forum: Desktop Environments
---

### Post by kapdon on 2011-07-17
Let me start off by saying that I am new here but have been using Ubuntu since 8.04. I am not very experienced and this is the first time I have tried writing a tutorial for this type of stuff so hopefully if anyone has any trouble following these steps perhaps someone more experienced could rewrite it and perhaps include some screen shots.

I do not know if anyone else has found this but I have search all over to find a way to add a panel to Unity and found nothing. Every forum I looked at argued that you can not use a panel with Unity and that if you wanted a panel you would have to use the classic desktop. I am able to get a panel working with Unity but I have to "launch" the panel every time I boot Ubuntu. This is how I did it.

First I followed installed the ClassicMenu Indicator by following the steps here [http://ubuntuguide.net/classic-menu-indicator-applet-in-ubuntu-11-04-unity-system-tray](http://ubuntuguide.net/classic-menu-indicator-applet-in-ubuntu-11-04-unity-system-tray) which has you do three easy copy and pastes into a terminal.

[FONT=Franklin Gothic Medium]sudo apt-add-repository ppa:diesch/testing 
sudo apt-get update 
sudo apt-get install classicmenu-indicator

This places an icon for the classic menu you are probably more familiar with in the notifications area (top right next to volume time)
If all you would like is a Menu button then stop here. However, if you would like a panel then keep reading.

Using the menu I went to Preferences>Main Menu

Once inside the Main Menu I clicked Accessories and checked the box marked Panel and closed the window.
I then launched the panel by going to the ClassicMenu indicator>Accessories>Panel 

The first time I did this it placed two panels on my screen. One at the top and one at the bottom. The one at the top was covering the Unity bar and causing a gap between my windows and the bar itself. It was also effecting the behavior of the Unity side bar, so I deleted it. The bottom panel can be customized how I like it. I deleted it once and added a new panel just to see if it worked and it did.
The only problem I have found is that the panel must be launched each time the system boots and if the bar IS NOT extended it causes screen placement problems. It often ended up right in the middle of the screen. But as long as the panel is extended, and not on top or on the left side of the screen it works pretty good and does not effect the Unity bars.

I also tried Alt+F2 to launch the panel but was not successful. I am only able to launch the panel from the ClassicMenu indicator. If anyone else is able to launch the panel somehow without using the ClassicMenu indicator please let me know how because I just do not like keeping a menu in my notifications area.


[/FONT]Hope this helps someone looking for a panel!

---

