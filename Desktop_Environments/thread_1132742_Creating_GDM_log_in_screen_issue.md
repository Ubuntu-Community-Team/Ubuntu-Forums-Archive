---
title: "Creating GDM log in screen issue"
date: 2009-04-22
forum: Desktop Environments
---

### Post by David C. on 2009-04-22
So I'm trying figure out what I did wrong here. 

I took an existing GDM log in file, downloaded one from art.gnome.org cracked it open and began my exploration. 

The goal is to create my own log in screen using a different .jpeg that I pulled from the web. I switched out the jpeg file with my own, renamed the xml file, only changing height="0"/  in the pixmap, it was previously set at "100%". I did this per the HowTo from gnome's site. I kept the icon .png files as is, I'll change them later. For now, I'm only looking to experiment and learn. I rewrote the GdmGreeterTheme, saving that with a .desktop file extension. Created the tar.gz file and installed it into the Login Window.

The error -- The image, within the Login Preference/Local, I installed doesn't show; it is a default image and beneath the theme title is  "null" 

I ran xnest to pull it up and got a default Gnome log-in screen, not the same Ubuntu brown that was in Local. I can't figure what I did or didn't do. I recreated the .desktop file as follows:

[GdmGreeterTheme]
Greeter=Alien.xml
Name=Alien
Description=Alien


I didn't include the author, copyright or screenshot, since this is for practice and personal use, and I won't be posting it to any site. And  per the HowTo, I was to take the screenshot from the xnest window and bring the screenshot into Gimp to reduce the size. I suppose once that was done, then I was to add it to the file and rezip it. Though I would need to redo the .desktop. I don't know if Screenshot=Alien.jpg in the .desktop file or not would be a cause.

I've attached a screen shot of the Log In Preference and xnest window so you can see what I'm getting.

Appreciate any guidance. Thanks.

---

### Post by David C. on 2009-04-22
Shamless bump, still looking for assistance. Thank you.

---

### Post by David C. on 2009-04-23
Hello? Is this thing on *taps screen* Hello? Can any one help?

---

