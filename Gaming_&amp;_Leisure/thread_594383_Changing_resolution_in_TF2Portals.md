---
title: "Changing resolution in TF2/Portals"
date: 2007-10-27
forum: Gaming &amp; Leisure
---

### Post by sfunk1x on 2007-10-27
I've installed Steam and can play a variety of other steam apps. Today, I installed TF2 and Portals, and I cannot see enough of the screen to get into options to change resolution. I am running 1280x720 on my desktop, but when TF2 or Portals launches, the resolution changes to something horrid and stretched.

Is there anyway to fix this at console, or do I have to delete them and reinstall? It won't be that bad, I guess.

---

### Post by The Noble on 2007-10-28
I'm assuming you are using wine? You may want to use a windowed mode, as fullscreen generally has some glitches like the stretching. I don't own the games personally, so I may just be shooting in the dark, but at least try that for starts.

---

### Post by stapler123 on 2007-10-28
In steam you can use launch options (i think you can do it from the terminal too)

 In the "My Games" tab you can right click the game and choose "properties"
From there click on the "Set Launch Options" button

in there you can set the options, if you check out steam related game threads here there is some info about what options to use.
[http://developer.valvesoftware.com/wiki/Launch_options](http://developer.valvesoftware.com/wiki/Launch_options) - thats also a good place to look
To set the resolution you need
-width 1280 -height 720

I run mine in a windowed mode so it doesn't stretch across both screen and use 
-width 1270 -height 690 -window  
With it slightly smaller than the actual size of the display I'm able to fit the whole window and window boarder in view.

---

### Post by sfunk1x on 2007-10-28
Just posting back that this solved the issue.

---

### Post by TuxTwig on 2007-10-31
Hmm might as well post here...how exactly do you change your screen res in Ubuntu. I only see the 1024*768, 800*600, and 640*480 options..

---

### Post by sfunk1x on 2007-10-31
What video card do you have installed - and if it's ATI or Nvidia, do you have the Restricted Drivers stuff installed? What version/distro are you running?

---

### Post by Multiplication on 2009-07-21
I have a similar, but more extreme problem. I've been playing tf2 on windows for a year on Windows, but when I switch to Ubuntu, I get it on wine, I fool around with it for a while, and I still can't get the main screen to appear. I've gotten as far as: bass hit plays, the Valve head shows, then the source message.  Then the screen goes black, and the mouse appears. After a few seconds the main screen's music starts playing. I move the mouse around and where the "Find Server, Create Server, etc" should be on the screen, I hear the clicking sounds of the mouse being over them. 
Everything seems to work, except the screen is still black, only the mouse is appearing. I am currently booting tf2 in a window. Please help, my clan is angry with me.

---

