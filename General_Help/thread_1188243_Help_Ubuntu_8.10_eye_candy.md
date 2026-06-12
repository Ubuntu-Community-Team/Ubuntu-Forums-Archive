---
title: "Help Ubuntu 8.10 eye candy"
date: 2009-06-15
forum: General Help
---

### Post by JAS510 on 2009-06-15
Hello,

I'm new to ubuntu and i have seen some nice eye candy stuff you can do w/ UBUNTU.  3d desktop, wobbly screen, and other stuff.

I loaded Ubuntu on a laptop dell d630.  Can you guys post up what i need to do so i can make my Ubuntu 8.10 look nothing like vista but everything like an open source system eye candy.  How do i load themes, how do i enable 3d desktop? how how how...

I dont know anything about terminal or any other cmdline.  

You help would be greatly appreciated...

thanks
If this works well, i will recruit more to join ubuntu.  :)

ps: can i load compiz and make things look really neat?

---

### Post by raymondh on 2009-06-15
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)
[http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

See is you can enable desktop effects (rt. click on your desktop > change desktop appearance > Visual effect ) and choose extra or normal.

Use synaptic (system > administration > synaptic package manager) and search  compiz settings manager.  Click the box and then apply.

See the links above for reference and have fun.

---

### Post by JAS510 on 2009-06-15
coool...i will try this at home and see where it gets me.

thanks.

---

### Post by raymondh on 2009-06-15
> **JAS510 said:**
> coool...i will try this at home and see where it gets me.

thanks.

You are welcome .... have fun and happy Ubuntu-ing :)

---

### Post by TrakerJon on 2009-06-15
Compiz

The default Ubuntu display setup lets you choose from None, Normal or Extra. Make it a lot more configurable with the CompizConfig Settings Manager...found in System > Preferences after installing the following from a termial window command prompt:
**sudo apt-get install compizconfig-settings-manager gnome-art usplash startupmanager compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald librsvg2-common fusion-icon**

ATI and Nvidia Drivers, Desktop Effects and Compiz

The new Ubuntu 9.04 Jaunty Jackalope system comes with a Nouveau display graphic driver by default and the advanced effects cannot be used. If you've already tried to enable restricted Ubuntu drivers and ATI/nVidia cannot be found in the list try installing the ATI/nVidia driver with this tutorial:

1. Run Applications/Add/Remove
2. From the left menu choose System Tools
3. Next from the right menu, find and select for install: Desktop Effects (Compiz Setup) and ATI/Nvidia binary X.org Driver (nVidia could be version 173 or 177). Selecting the driver will get the list of supported graphics cards.
4. Click Apply Changes and after installation go to System/Administration/Hardware Drivers
5. The system will search for available drivers, choose the recommended option from the list and activate the driver by clicking Activate.
6. Restart your system and the new ATI/nVidia graphic display driver will be in use.
7. See Compiz above.

---

### Post by JAS510 on 2009-06-15
Guys,

I was able to do all the following steps mentioned with success.  I got my screenlets, OSX doc, and do some pretty cool stuff when i minimize, close, open windows.  This was real simple.  I love it.  

I saw something on youtube where you can have an animated background and actually rotate the cube. (it looks like the camera is pulled out and you can see behind the cube)  Oh and loading some new themes.  I saw some drag and drop procedures to loading themes but is that it???? That seems too easy! :)

Either way, i'm loving this new O.S.  Its shitting on Windows!!!

---

### Post by raymondh on 2009-06-15
> **JAS510 said:**
> Guys,

I was able to do all the following steps mentioned with success.  I got my screenlets, OSX doc, and do some pretty cool stuff when i minimize, close, open windows.  This was real simple.  I love it.  

I saw something on youtube where you can have an animated background and actually rotate the cube. (it looks like the camera is pulled out and you can see behind the cube)  Oh and loading some new themes.  I saw some drag and drop procedures to loading themes but is that it???? That seems too easy! :)

Either way, i'm loving this new O.S.  Its shitting on Windows!!!

Hello JAS510,

Congratulations.  Have fun experimenting :)

---

