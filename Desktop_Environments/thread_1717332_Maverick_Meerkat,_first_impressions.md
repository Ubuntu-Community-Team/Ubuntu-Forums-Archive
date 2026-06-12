---
title: "Maverick Meerkat, first impressions"
date: 2011-03-29
forum: Desktop Environments
---

### Post by Do_Japan on 2011-03-29
I recently created a new system and decided to try Ubuntu 10.10 x64.  My  overall impression of the OS has been bright, however I have found the  experience to be rough around the edges.  Being new to linux I am  posting a summary of my first impression.  I hope to compare my  experience to the experiences of others to determine if some of the  issues I've had can be resolved or if they are due to the fact that I  paid nothing for the software that probably took thousands upon  thousands of hours to develop.
After a month of tweaking the system I  am still trying to wrap my head around an issue that is causing the  system to freeze about once a day.  When the system locks up music  continues playing (for the remainder of the track) and I can still move  the cursor but cannot click on anything.  The system will only respond  to the CTRL ALT SYSRQ REISUB command at that point.  I realize that a  lot of the free media software I use is still in a development stage,  but since linux is inherently rock steady I wouldnt expect bad programs  to hangup the entire system.  Might this issue be due to the fact that  I'm a heavy user and frequently have over 20 programs running across 4  desktops?  My other thought is that there is an issue with a hardware  component.  I put a used HDD into my new system and wouldn't be  surprised if it is damaged, though disc checks never report any problem.
I've  had other buggy issues that are mostly just annoying.  Sometimes the  system menu and menus within programs will get stuck open and display  their outline until I go back and open them, then close them.   Additionally, sometimes menus just wont respond to clicking until I back  off and wait a few seconds.  Might there be a problem with my mouse  (never had any problem clicking on things in windows) or just gnome  bugging out?
Finally, although the new graphics card I got with the  system is cheap, because I upgraded from an archaic AGP card to a PCI  Express card I was expecting a world of difference in terms of video  performance.  This is proving not to be the case at all!  If I increase  the Visual Effects from the Appearance window to anything higher than  "No Effects" the system becomes slightly laggy and almost 4x unstable  (freezing multiple times a day at that point).  The card is GeForce 210  (650 mhz GPU, 512mb DDR2).  I wasnt expecting to play Modern Warfare 2,  but I at least hoped to pull off the desktop cube.  Alas, the system has  been far too unstable for that.  Do desktop visual effects (like the  cube) require an elephant of a video card or what?
Other than these  issues, I've found Ubuntu to be a tremendous tool with tons of free  software bonuses.  I also enjoy the way certain programs (such as Wine)  seamlessly fold themselves into the GUI.  I'd appreciate hearing from  others about these issues.  Are these common experiences?  Do my issues  seem hardware/software related?  Is there a specific error log I should  be checking after the system freezes to narrow down the cause?

---

### Post by VastOne on 2011-03-29
Any of these processes a Flash video when it freezes?

Is there any pattern at all to the freeze ups?

---

### Post by Do_Japan on 2011-03-29
I had noticed that Firefox is often the active program when the system freezes, but not always.  Flash seems to work great in Firefox, I don't notice any instabilities that are specific to flash.  The system has frequently hung when scrolling through pages of google image search results, might google image search use flash?

---

### Post by JoeTheDude on 2011-03-29
For the random freezing, I had this problem too. Turns out my swap partition was defaulted to off whenever I started up Ubuntu. Open up your System Monitor and look at your swap usage. If it says "0 of 0 bytes" or something similar, then it is not enabled and your computer will likely hang when you use up all of your physical RAM. To enable your swap, open the terminal and execute:
```
sudo swapon -a
```
You should see your swap start to work properly in System Monitor and the freezing won't happen anymore.

Now as I said, this will probably reset when you reboot your computer. To fix this permanently, check this thread out: [http://ubuntuforums.org/showthread.php?t=826912](http://ubuntuforums.org/showthread.php?t=826912)

---

### Post by Do_Japan on 2011-03-29
Thanks for the idea.  I have never noticed the swap partition in use in system monitor, it always shows 0% of 1 GB.  Never needed it with 4 GB of RAM, the most I ever used was 2.  But I made sure swap is turned on and will see if things improve.

---

### Post by IWantFroyo on 2011-03-29
Ubuntu is (in my opinion) amazing. The only reason people have problems is the manufacturer tailoring. They specifically design the laptops for Windows 7, and then edit the Windows 7 for the laptop.
I would recommend putting any questions you have into the forum individually, and email-following them.
Good luck!
PS - desktop cubes work just fine on computers that don't even have drivers for the video card activated. I don't know why you are having difficulties.

---

### Post by Do_Japan on 2011-03-29
I'm not using a laptop.  I will try enabling desktop cube one more time with swap turned on (it actually forced me to use a driver to even enable effects), if it hangs I might try an older version of ubuntu (10.04, 9.10, 9.04, what do you guys suggest? anybody noticed stability difference between x84 and x64 architecture?).  I'm also using the proprietary nvidia driver that downloaded automatically, I'll look for different drivers, if they exist.

---

### Post by Do_Japan on 2011-04-01
I turned on graphics effects and desktop cube again, it didnt take 10 minutes for the system to freeze.  Can others confirm that the desktop cube works fine without a powerful graphics card or drivers?  It seems that I might as well try an older version of ubuntu.  Does anyone have a recommendation as to which version might be the most stable with a geforce 210?  Any performance difference between the x84 and x64 versions?

---

