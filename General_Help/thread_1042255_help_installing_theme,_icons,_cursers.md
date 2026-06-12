---
title: "help installing theme, icons, cursers"
date: 2009-01-17
forum: General Help
---

### Post by deesenuts on 2009-01-17
so, go easy on me, it's my first post.  i looked at many other somewhat related posts which didn't answer my questions before posting this.


i'm trying to install an overglossed theme i saw [**[COLOR="Blue"]here[/COLOR]**]("http://maketecheasier.com/10-of-the-best-linux-desktop-customization-screenshots-to-inspire-your-creativity/2008/11/28")(it's the first one in that list.)
1) i got the emerald theme installed, but it doesn't glow and isn't transparent like in the picture.
2) i downloaded the icons but can't get emerald or sys-pref-appearance to recognize them.
3) the wallpaper works (i'm so l33t :roll:)
4) the awn theme works but doesn't have the icons like in the screenshot
5) i'm having the same problem with the cursors that i am with the icons

thanks for your help.

i'm using intrepid on an hp dv2000 if that helps.

---

### Post by Wartender on 2009-01-17
ok for the transparency you have to install compizconfig settings manager (from system->administration->synaptic package manager) and in the opacity, brightness and satuarion plugin edit the settings to your liking.
for the icons how are you installing them? try dragging the .tar.gz (or.tar.bz2 or whatever) onto the MAIN WINDOW of appearance, as in open it, don't touch anything and drag the COMPRESSED file (not the extracted folder) onto the window, if his doesn't work, go to your home directory, press ctrl+h and go into your .icons directory and copy the extracted folder there, see if you can change it, everything i just said aplies for cursors as well, in awn just right-click the application icon and choose "change icon" go to your .icons and select the image you want (it's kind of annoying you have to do it for every application for which you want to change the icon)

---

### Post by FAMUgolfer on 2009-01-17
For cursor issues:
1. Unpackage your desired cursor into /usr/share/icons (if its already unpackaged just cut and paste that folder by opening a terminal and type....sudo nautilus...then navigate into the /icon folder.
2. System>Preference>Appearance>Customize>Pointer Tab>.......and select your desired cursor

For icons:
1. Unpackage your desired icon into /usr/share/icons....just like the directions for cursors
2. System>Preference>Appearance>Customize>Icon Tab>....and select your desired icon theme

PS. I think that Black & White overglossed theme needs to be unpackaged twice to get to the actual folder(weird)

Hope this helps!!

---

### Post by deesenuts on 2009-01-18
thank you so much!
everything works except for the glow around the windows.  i don't know which setting i would find that option in.

a different problem appeared after i installed the theme: in compiz config settings manager i can see the icon, but i can't see the name of each of the plug-ins (is that what they're called?) unless i hover the mouse over them.  it seems like the theme caused the background color of the button to be the same as the text color until the mouseover event, any suggestions on how to fix that?

thank you for your help

---

### Post by techturkey on 2009-01-18
I am having problems with emerald but go to the edit theme tab in the manager and there should be a check box at the bottom of the window. 

Hope this help and im not totally clueless :D

---

### Post by deesenuts on 2009-01-18
yeah, i have both the use button halo/glow and the use button halo/glow for inactive windows selected, but still no glows or halos on anything

---

