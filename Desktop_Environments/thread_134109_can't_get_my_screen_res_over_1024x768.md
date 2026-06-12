---
title: "can't get my screen res over 1024x768"
date: 2006-02-21
forum: Desktop Environments
---

### Post by pullathomas on 2006-02-21
I installed 5.10 with a desperation to get off of windows.  i am fairly familiar with linux and generally am pretty good at picking new stuff up. i installed 5.10 on an intel 910 chipset, to come on the forums and realize that many people were having a problem with the driver and getting their res over 1024x768.  so i installed in another machine, an older machine, still had no luck.  then i downloaded the beta 4 of Dapper (6.04) and installed in on the original 910chipset.  Dapper had the proper drivers installed them and the install, updates and additional added programs installed great.  yet, my screen resolution is still at 1024x768.  normall this wouldn't be a problem but i had a 24in widescreen lcd that i would like to take full advantage of.  can anybody help me out with this?

---

### Post by heimo on 2006-02-21
Have you tried 855resolution? And adding vertrefresh/horizsync lines and a custom modeline? 
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by jones_jj on 2006-02-21
First, what is the screen resolution for your LCD monitor?  What is it able to handle?  Also have you to run the dpkg-reconfigure xserver-xorg application to set up your monitor and video card?

To run this application you have to first log into root:  first press **ctrl+alt+F1** and log into root, next run **dpkg-reconfigure xserver-xorg** and go through the screens.  Make sure you know the amount of memory on your video card, and it has to be in KB not MB.  After you go through the screens, press **ctrl+alt+F7** to go back to your normal GUI login screen.  Then reinitialize the screen by pressing **ctrl+alt+backspace** and that should enable the full range of resolutions that you enabled using dpkg-reconfigure xserver-xorg application.

Hope this helps.

---

