---
title: "trying to set desktop effects, will no longer boot"
date: 2008-01-30
forum: Desktop Effects &amp; Customization
---

### Post by eternalthree on 2008-01-30
Hi, I've installed gutsy gibbon over the weekend and i'm slowly getting the hang of things til i got completely sidetracked tonight. 

I was in the appearances menu, trying to set the graphics to a higher setting for desktop effects. gutsy told me something about installing nvidia drivers and then requiring a reboot. After this, it would not boot anymore. The computer gets to the part where the OS starts loading, but before it prompts me for a user/pass, my lcd turns off. if i hit the power button on my tower, the terminal shows up, shutting down processes, and then the desktop shuts off.  

i'm kinda lost. i'm a fairly windows literate user, sadly, and linux is a fully different language, like relearning dos almost (which was ..... wow, painful)

any help would be much appreciated as i am not even sure where to go now. 

Gutsy Gibbon 7.10
Intel E6300
Biostar TForce 965PT
2GB GSkill Ram 800
XFX geforce 7950GT 512MB
80GB WD IDE HD
Samsung 16x DVDRW

Thanks again. =)

---

### Post by chewearn on 2008-01-30
1. Power-up the PC, after BIOS POST, when you see message "press [ESC] to ..." something like that, press ESC key.  You should see the Grub menu screen, select recovery mode, press enter to boot.

2. You should be brought into a root console.  Then run:
```
nvidia-xconfig
```

3. Then, reboot by:
```
shutdown -r now
```

---

### Post by eternalthree on 2008-01-30
Hello, Thank you for the response. Much appreciated. Just got home and tried your advice without any success, same issue.

I ran the command line as you stated and it backed up the file. I took a look at the file itself and nothing seems out of the ordinary. (at least i probably dont understand it)

When I rebooted , it did the same thing, the ubuntu logo shows up, starts loading, and when the bar is finished and it looks like its going to start up, BAM - the LCD turns off and I cant see what's going on anymore. If i hit the left/right keys, the internal speaker will beep at me, but not if i press up or down. 

Anyway, If i hit the power button once at this point, the lcd will power itself back on and show me the terminal as it shuts everything down and then a few seconds later, the system is off. 

Any more suggestions? I might have to go to osx86 next week when my ide to sata adapter arrives, haha. or maybe i'll just keep trying both. Ubuntu is a fun challenge so far, and I wanted to try some of the apps on lifehacker's top ten ubuntu apps. Thanks again for your time, Have a good one.

---

### Post by chewearn on 2008-01-31
It's quite likely that the nvidia graphics card is trying to drive at higher resolution or frequency that can be supported by your monitor.  As to how to fix that, there are some possibilities, but I'm not quite sure which will work.  As a start, could you post your /etc/X11/xorg.conf

(You can copy out this file from your PC but booting into recovery mode again, then copy the file to a usb drive).

---

### Post by wesley_of_course on 2008-01-31
I've used " Envy " before and it worked for me . Have you tried it ? 
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

 Hope this helps .

---

