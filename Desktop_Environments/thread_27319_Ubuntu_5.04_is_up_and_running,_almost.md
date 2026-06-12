---
title: "Ubuntu 5.04 is up and running, almost"
date: 2005-04-15
forum: Desktop Environments
---

### Post by Giturar on 2005-04-15
Alright, I have Ubuntu running at pretty much full capacity, but there are couple things that need install and/or fixed.

1) GFX - Right now I have an eVGA FX5200 graphics card. Not up-to-snuff by any means, but it does its job for now. I installed the nVIDIA drivers without problems, and ran glxgears. Unfortunatly, I was only getting ~400-450 fps. Is this normal for this card? Or should I be getting much higher?

[EDIT]: I rebooted and now I'm getting 1200 fps, which seems a little more normal.

2) Cedega - Alright, I still have WinXP because I still play World of Warcraft (even with the FX5200, runs fine at low res), and from what I heard it works good under Linux using Cedega. One of my friends (who uses debian), had a copy of cedega, so he let me borrow it to install (just for the record I do support programmers efforts, but since they dont offer a demo of cedega, I didnt want to pay $15 if the program wasnt going to work). Anyway, I install it, and try to install WoW, but it errors out telling me there are several LANGs that are 'en' and that I should change the LANG enviroment variable to en_US. Well how do I do this?

3) Wine - Since Cedega didn't end up working, I tried installing Wine. I installed Wine, winetools, and winesetuptk. I ran winetools and started the installation. It ran fine until the end of the first step, where it errored out due to it not being able to find "wineboot." I then tried to run it using sudo, but got the same error. So I'm not sure where to go from here in that respect.

[EDIT]: Got it working using winesetuptk rather than winetools

4) Logitech Special Buttons - I have an Elite keyboard and an MX700 mouse, both of which have special buttons (play, stop, volume on the keyboard; forward, back, autoscroll on the mouse). Is there a way I can get these buttons working?

5) I have my guitar plugged into the Line-In on my sound card (Audigy2 ZS), and in Windows, this caused the the sound to go direct to the speakers. How can I do this in Linux? The reason I do this is becuase my old amp broke, and I dont have a new one yet, plus I used to record using the line-in, so I could record and hear what I was recording through the same source.

6) Buttons and Checkboxes - In firefox, the buttons, checkboxes, pull-down menus, etc all look pretty ugly. Is there a way to clean these up?

7) Eye Candy - Looking at the desktop right, its very clean and whatnot, but are they any eye candy effects I can install? For example, when I autohide the menu, it smoothly scrolls out instead of just pops up, or inactive windows fading transparent until I hover over them. Anything like this?

[EDIT]: Fades looking good

8) Terminal Transparency - When I set the transparency in the terminal, it shows only the desktop. If there are any windows behind the terminal, they dissappear, and only the desktop wallapaper shows through. How can I get the terminal to show everything underneath it when its transparent?

[EDIT]: Just set a bg pic, xcompmgr didnt do anything for this

I think thats all for now, Ill post more when (or if) anything else comes up.

Thanks in advance!

---

### Post by philipacamaniac on 2005-04-15
4. You have to enable special buttons: [http://www.ubuntuforums.org/showthread.php?t=27039](http://www.ubuntuforums.org/showthread.php?t=27039)

5. Your volume mixer (eg., alsamixer or the GNOME mixer) should have a Line-In fader. Simply turn it up. I have an Audigy2, but I'm using Kubuntu/KDE, so I don't know the GNOME mixer.

6. Install a better looking Firefox theme: [https://addons.update.mozilla.org/themes/?os=Linux&numpg=10&application=firefox](https://addons.update.mozilla.org/themes/?os=Linux&numpg=10&application=firefox)

7. Enable xcomp extensions: [http://www.ubuntuforums.org/showthread.php?t=20769](http://www.ubuntuforums.org/showthread.php?t=20769)

8. See #7 (I think)

---

### Post by Giturar on 2005-04-16
Alright, the media buttons work, except play. Since the play button and pause button are the same, I can pause, but cant play again, any fix to this?

---

### Post by vapor on 2005-04-16
[QUOTE=Giturar]Alright, the media buttons work, except play. Since the play button and pause button are the same, I can pause, but cant play again, any fix to this?[/QUOTE]
 I was able to get my ms desktop elite keyboard to work using the following program and info:

[http://lineak.sourceforge.net/](http://lineak.sourceforge.net/)

---

