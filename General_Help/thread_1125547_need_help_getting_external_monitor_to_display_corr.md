---
title: "need help getting external monitor to display correct resolution"
date: 2009-04-14
forum: General Help
---

### Post by originalsynthesis on 2009-04-14
Soo, im using a laptop right now with a broken screen :(. It is an older toshiba satellite with an extra large screen. ( 1280 x 768 ) I was using an even older Proview monitor so i could use this machine.  For some reason, I never had much trouble using this particular monitor with linux, yet when i tried other monitors there was always an issue with the xserver not knowing that it should display at the appropriate res for the monitor itself, and not to display in the laptops' screen resolution.  
  Anyway, the old Proview juggernaut is starting to fritz out and i need to get my new display working. I got an HP pavilion f1503 flatscreen monitor and it too is (as i type this) getting the wrong res sent to it. All i can see right now of Firefox is the text box im typing into. I've tried fiddling with all the options in the Nvidia x server settings to no avail. I'm using Ubuntu Heron. Any suggestions?

---

### Post by LowSky on 2009-04-14
in terminal tpye

gksu nvidia-settings

change the display settings to the monitor normal resolution which is 
1024 x 768 at a 75 Hz  dont forget to save XORG and reboot

sorry it wont run 1280 x 768

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00036535](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00036535)

---

### Post by originalsynthesis on 2009-04-14
when i tried the gksu nvidia settings, it prompted for my password and then did nothing. is there another command i need to know?  

BTW, i went into the nvidia settings gui. noticed that it doesn't seem to recognize the monitor im using. It gives the option to use either the nvidia default flatpanel ( 1280x768 ) which i would assume is my laptop's display, or the CRT-0, which only gives the res options auto, 640x480, or 320x240. I have the flatpanel set to 'disabled'

---

### Post by originalsynthesis on 2009-04-14
whoops, redundant reply, that one. i just missed the '-'. But yeah, cant set it to 1024. should i set the flatpanel maybe?

---

### Post by originalsynthesis on 2009-04-14
using the gksu command you gave,i tried undisabling the default flatpanel and setting it to 1024x768. couldnt' get more than 60hz, so i set to auto. saved to xorg and cntl alt bkspcd. no change.

---

### Post by originalsynthesis on 2009-04-14
I switched back to the old Proview monitor and checked the nvidia settings.  After xrestart, it immediately recognized the monitor as 'proview'.  and curiously, it works optimally at 1280x768. Now, im almost certain that the monitor's actual max rez is 1024x768.  What this is telling me is that i need to figure out how to get ubuntu to recognize my hp monitor. Anyone know how to do that?


Now i know this is possible: I just unplugged the working monitor and plugged in the Hp flatscreen, without xrestart, and the settings for the proview work perfectly on the hp. so does ANYONE have any ideas? maybe some kind of manual edit to xorg?

---

