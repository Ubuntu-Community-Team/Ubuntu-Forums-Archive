---
title: "How to put custom minimize,maximize,close buttons on window borders."
date: 2012-03-16
forum: Desktop Environments
---

### Post by adamgray1337 on 2012-03-16
How to add custom buttons on the window border without changing the window border? For example I want to put the green, yellow and red mac buttons (minimize,maximize,close) from my mac window border on my clearlooks window border without having to change to the mac window border.

---

### Post by mraandtux on 2012-03-16
Ubuntu tweak and GNOME Tweak tool will help.

---

### Post by adamgray1337 on 2012-03-16
Thanks for leading me in the right direction, but now I have another problem. When I search for ubuntu-tweak or gnome tweak tool in the software center it shows no results.  When I download ubuntu-tweak or gnome tweak tool from the web sites it directs me to the package in the software center where the  install button is grayed out and unclickable. I am running ubuntu 10.10 Maverick Meerkat. Any suggestions?

---

### Post by cortman on 2012-03-16
> **adamgray1337 said:**
> Thanks for leading me in the right direction, but now I have another problem. When I search for ubuntu-tweak or gnome tweak tool in the software center it shows no results.  When I download ubuntu-tweak or gnome tweak tool from the web sites it directs me to the package in the software center where the  install button is grayed out and unclickable. I am running ubuntu 10.10 Maverick Meerkat. Any suggestions?

Gnome-tweak and Ubuntu-tweak are for Gnome Shell and Unity, respectively. Maverick comes with neither installed; you're using Gnome2 unless you manually installed either of the other two.
I know in Gnome shell you can edit the GTK theme located in /usr/share/themes. It's probably similar in Gnome 2.

---

### Post by adamgray1337 on 2012-03-17
So then I can't use ubuntu tweak or gnome tweak tool unless i update to unity? That sucks. But now I am confused. I went to home/.themes and I noticed that inside the folder for my mac theme was a metacity-1 folder with all the icons used for the theme including the yellow green red  (minimize, maximize, close) buttons in the folder. However my clearlooks folder only had gtk folder with only a document inside of it. So I am back to my original question, how do I put custom mac minimize maximize close buttons on my clearlooks window border?

---

### Post by cortman on 2012-03-17
> **adamgray1337 said:**
> So then I can't use ubuntu tweak or gnome tweak tool unless i update to unity? That sucks. But now I am confused. I went to home/.themes and I noticed that inside the folder for my mac theme was a metacity-1 folder with all the icons used for the theme including the yellow green red  (minimize, maximize, close) buttons in the folder. However my clearlooks folder only had gtk folder with only a document inside of it. So I am back to my original question, how do I put custom mac minimize maximize close buttons on my clearlooks window border?

Sorry, I'm really not that knowledgeable about theming Gnome2. I'm guessing, however, that some CSS or similar document for drawing the window theme is referencing those icon files. What you could try is making your own custom buttons, place them in the folder with the other icons, and give them the same filename as the existing icons (rename the old icons filename.old so you'll still have them) then reload the desktop and see if that works.

---

### Post by drlmg on 2012-04-07
They disappeared completely on all of my desktops and laptops with a recent update. How can I get them back?

---

### Post by typhoon_tip on 2012-04-07
Easiest way to do what you want is to install Emerald Window manager, on Ubuntu 10.10. You will find the Emerald package in Synaptic and Software Center.

Then, you can download MAC4LIN theme (you will find plenty of reference around), and you can customize your theme as you want, from full MAC look to just icons and borders.

---

