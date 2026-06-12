---
title: "Dockbarx and XFCE 4.10?"
date: 2013-02-24
forum: Desktop Environments
---

### Post by LoganJ85 on 2013-02-24
I have a kinda old netbook, so I am running Xubuntu 12.10 and I want to use DockbarX. I found instructions online, I don't quite remember what commands I had to run it but I believe it was just apt-get install dockbarx and dockbarx-plugin (or something similar to that, I really cant remember).

Anyhow, at the moment I can go to menu -> accessories -> dockx (also have dockbarx preferences, but I have not yet found anything to solve my problem in there) and it will load dockbarx vertically along the side of my screen. But that is not what I want, I want it in my panel.

While searching google, I also noticed that it was suggested to install xfce4-xfapplet-plugins, but when I attempt to do so I get an error message stating "E: Package 'xfce4-xfapplet-plugin' has no installation candidate" , I am not sure what that means.

Searching google also seems to reveal positive results for DockbarX and XFCE 4.8 but I cant find anything for 4.10. Is DockbarX compatiable with XFCE 4.10? If not, can I downgrade to 4.8?

---

### Post by Frogs Hair on 2013-02-24
I am using Dockbarx in the XFCE 4.10  Session. I will login to XFCE and edit this post.

Edit: I have Dockbarx 0.90.3 installed via PPA and in Preferences > Dock there is location setting. If you are not seeing this you may be running a different version. I also use the XFCE session and not Xubuntu.

---

### Post by LoganJ85 on 2013-02-24
Frogs Hair- I don't remember the commands I used to get Dockbar X, but I believe I did have to add a PPA, and my version of DockbarX is 0.90.3

I did find the very same setting page that you have, but simply put I think I will let the picture explain:

[http://imgur.com/wRyS5ZX](http://imgur.com/wRyS5ZX)

(I uploaded it to imgur, despite being only 31kb, it is 1920x1080 and that resolution appears to be larger than what the forum wants for attachments, and I am not yet sure how to resize images on this pc)

Basically, if I open DockX, it loads vertically along the left side of the screen, and appears to work well, but that is not the location I want it. I want it on the bottom, inside my panel, between my menu and clock and everything else. I cant quite tell from the settings, do I need to find a way to add DockbarX to the existing XFCE panel? Or do I need to move the menu and everything else to DockX, and relocate DockX to the bottom of the screen?

---

### Post by nilarimogard on 2013-02-25
DockBarX doesn't support the Xfce panel yet and the  xfce4-xfapplet-plugins package has been removed from the Ubuntu repositories starting with Ubuntu 11.10 Oneiric Ocelot (that plugin allows embedding apps into the panel like they were applets).

---

### Post by LarsKongo on 2013-02-25
See answer above. But you can fake it a bit. Create 2 xfce panels and position them bottom-left and bottom-right. Make the panels 100% transparent. Add the main xfce menu in the bottom-left panel and anything else you want in the right.

Place dockx centered at the bottom of the screen, panel mode off. Use Gimp to create and integrate a background image on your wallpaper. Or you can use dockx background style in panel mode, but that will require compiz *(or any wm that can do the following)* with the setting to display xfce panels always on top.

Here's a quick example I threw together:
[ATTACH]231894[/ATTACH]
Xfce-panel with the main menu and an invisible separator at the bottom-left. The rest is dockx (panel mode and offset a few pixels) with a clock applet on the right.

---

### Post by Frogs Hair on 2013-02-25
> **LoganJ85 said:**
> Frogs Hair- I don't remember the commands I used to get Dockbar X, but I believe I did have to add a PPA, and my version of DockbarX is 0.90.3

I did find the very same setting page that you have, but simply put I think I will let the picture explain:

[http://imgur.com/wRyS5ZX](http://imgur.com/wRyS5ZX)

(I uploaded it to imgur, despite being only 31kb, it is 1920x1080 and that resolution appears to be larger than what the forum wants for attachments, and I am not yet sure how to resize images on this pc)

Basically, if I open DockX, it loads vertically along the left side of the screen, and appears to work well, but that is not the location I want it. I want it on the bottom, inside my panel, between my menu and clock and everything else. I cant quite tell from the settings, do I need to find a way to add DockbarX to the existing XFCE panel? Or do I need to move the menu and everything else to DockX, and relocate DockX to the bottom of the screen?

Are saying that when you change the _position_ setting displayed in the screenshots the panel doesn't move ? 

You can also center the panel in the settings as well if you don't want it to take up the entire length of what ever side you choose. I also have removed the bottom panel because I am using a dock. [http://ubuntuforums.org/picture.php?albumid=1718&pictureid=8586](http://ubuntuforums.org/picture.php?albumid=1718&pictureid=8586)

---

### Post by LoganJ85 on 2013-02-25
I have decided to use the solution LarsKongo provided. However, I was unable to find a way to have the dockbar centered and also strech across most of the screen, what I ended up doing was setting it as a panel along the bottom, and offset 95 pixels to allow for my XFCE panel with the menu. The only slight issue I have now is that the XFCE panel's width is defined as a percentage, so if I use the netbooks display it needs to be 10% to fit close to 95 pixels, but if I plug in my external 1920x1080 display, the XFCE panel needs to be only 5%. Unless I can specifically tell the XFCE panel to be 95 pixels wide, I can just put up with this. Afterall, I don't use the external monitor that much.

I am considering switching to a different window manager simply because I have no strong attachment to XFCE, I only use it because my netbook is slow. Does dockbarx play better with either LXDE, KDE, or Gnome?

---

### Post by Frogs Hair on 2013-02-25
Dockbarx has some recommended gnome dependencies when I view properties in synaptic. As written I use the session installed on Ubuntu and the not Xubuntu and that may explain why it why it works for me. KDE is somewhat heavy and LXDE is lightest.

See nilarimogard's post, I believe he/she is involved with the project via webupd8.    [http://www.ubuntuupdates.org/ppa/webupd8](http://www.ubuntuupdates.org/ppa/webupd8)

---

