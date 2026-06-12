---
title: "Softwares for panel?"
date: 2010-04-20
forum: Desktop Environments
---

### Post by Kognit on 2010-04-20
Hi!

Does anybody know if there exist any softwares for reconfigurations of the panel? 

Thx for help

Bye

---

### Post by johny_ on 2010-04-20
What are you trying to achieve more precisely? The panel can be configured within gconf in Ubuntu. Maybe there is this nice tool called "Ubuntu Tweak" that may help. Check it out

---

### Post by Kognit on 2010-04-20
thx for reply

I want to make a panel more rounded with panel edges etc. To play around :)

Any softwares that gives you a lot of freedom?

---

### Post by mcduck on 2010-04-20
> **Kognit said:**
> thx for reply

I want to make a panel more rounded with panel edges etc. To play around :)

Any softwares that gives you a lot of freedom?

Sorry, but Gnome-panel doesn't have such options.

Although you *can* set a panel background image, and if you make the image the exact size your panel is you can get it to look like it has rounded corners, and whatever details you might want. Gnome-panel supports PNG and SVG images which both allow for transparency (although you won't get real transparency as in being able to see your windows etc. behind the panel, instead it just uses your wallpaper image to fake the transparency).

---

### Post by Kognit on 2010-04-20
I have seen in gnomelook.org that custom panels could be created. Is there any software out there for this purpose?

---

### Post by mcduck on 2010-04-20
> **Kognit said:**
> I have seen in gnomelook.org that custom panels could be created. Is there any software out there for this purpose?

Any graphics application you know how to use will do the job. I prefer Inkscape, as vector graphics applications are well suited for this kind of purposes, but you can just as well use Gimp or whatever you like to use.

The panel background is just a normal image file, so you don't need any special tools to make one.

---

### Post by Kognit on 2010-04-20
About the background picture i know. But i don't know how to reconfigure panel because i don't know the exact folder/file locations of the panel to put it in. Any help?

---

### Post by mcduck on 2010-04-20
> **Kognit said:**
> About the background picture i know. But i don't know how to reconfigure panel because i don't know the exact folder/file locations of the panel to put it in. Any help?

There is no such things.

Just put the image where ever you like, right-click on your panel and select  "properties". You'll be able to set the background image there. Actually you can even just drag&drop your image to the panel to set it as panel background image.

(If you have problems doing this, make sure you are right-clicking on the panel itself, not any applet/icon that is running in the panel).

For the few advanced options the panel has just hit Alt-F2 and tun "gconf-editor", use that to browse to apps/panel and set the options there. For example to rotate the background image for vertical panels, or scale smaller images to fit your panel, you'd go to apps/panel/toplevels/*name_of_your_panel*/background. But as long as you make your image the same size your panel is, you don't need these options.

---

### Post by Kognit on 2010-04-20
ahhh, get it. I am really stupid. Thx for your help. I will report my results :)

---

### Post by Kognit on 2010-04-20
Thanks, MCDUCK. I was playing a bit with the photoshop and the inkscape and i managed to create the panel i have wished for days though it has to undergo some corrections. Thank you very much and have a nice day :)

---

### Post by mcduck on 2010-04-20
Great that you got it working. And good day to you too. :)

By the way, if you have problems with some applets not using the background image you set yourself, that's because the GTK theme you are using defines a background for them. In that case you'll have to edit the GTK theme and remove any panel theming from it. If you are lucky the theme has a separate "panel.rc" file which you can simply rename or delete...)

Gnome's panels (and also Gnome itself) is far more customizeable than it appears to be. The sad thing is that all the features are nowhere to be seen in menus and configuration options and might sometimes be quite hard to figure out. Like the animated wallpapers and all the neat stuff you can do with the panels.. Quite a lot can be figured out just by browsing the available options in gconf-editor, others you can only really find out if you happen to read about them on random Internet forums and web pages..

---

