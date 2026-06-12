---
title: "Screen resolution (yeah, again)"
date: 2005-05-04
forum: Desktop Environments
---

### Post by ultima2k on 2005-05-04
As probably all other people I wanna get a larger resolution than just 1024*768.
Edited "/etc/X11/xorg.conf" and added "1600x1200" "1280x960" like your suppose to, but it's just de same choises at the "Screen resolution preferences".

And yes I have tried restarting and so on.

Why wont it work? :S

---

### Post by c_dog on 2005-05-04
Most likely because even though you are telling it do a certain mode, if the DDC doesn't know what to do with it for your particular card and monitor it will only let you use VESA modes. This is usually happens when monitors are not entirely playing fair when comes to plug-n-play with your system. The video card is not automatically able to determine what the monitor is capable of. In this case you won't be able to use higher than VESA resolutions until you define *modeline*  in xorg.conf for your paticular monitor for each of whatever resolutions, color depths, and frequencies that you are plan on using.

---

### Post by ultima2k on 2005-05-04
Ok, I don't understand anything of what you just said :S

---

### Post by lorap on 2005-05-04
hi friend.
i've the same trouble.
just reinstalled warty (previous version) back,got the hell tired by trying to solve this difficulty. donno it worked well in older version why wouldn't it work now really donno.

---

### Post by Mat10 on 2005-05-04
Folks, after manually adding your preferred resolutions, take a look at the top task bar and select >system>preferences>screen resolution   be sure and tick the options box "Make default for this computer only"   if your desired resolution is showing.  This fixed mine from returning to lower resolution.


Tom

---

### Post by ultima2k on 2005-05-04
Mat10: as I wrote I can only select the default-resolutions after I have edited xorg.conf. That's the problem.
There's only 1024/800/640 and 60Hz, nothing else and even after I added 1600x1200 and 1280x960 they won't show up there.

---

### Post by maruchan on 2005-05-04
Modeline generator:

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

---

### Post by Tsjoklat on 2005-05-05
[QUOTE=ultima2k]As probably all other people I wanna get a larger resolution than just 1024*768.
Edited "/etc/X11/xorg.conf" and added "1600x1200" "1280x960" like your suppose to, but it's just de same choises at the "Screen resolution preferences".

And yes I have tried restarting and so on.

Why wont it work? :S[/QUOTE]

Setting it up through your Gnome/KDE doesn't always work, try hardcoding it in your xorg.conf.

Example:
        DefaultDepth    24
#       SubSection "Display"
#               Depth           1
#               Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x 400" "640x480" "640x350"
#       EndSubSection
#       SubSection "Display"
#               Depth           4
#               Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x 400" "640x480" "640x350"
#       EndSubSection
#       SubSection "Display"
#               Depth           8
#               Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x 400" "640x480" "640x350"
#       EndSubSection
#       SubSection "Display"
#               Depth           15
#               Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x 400" "640x480" "640x350"
#       EndSubSection
#       SubSection "Display"
#               Depth           16
#               Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x 400" "640x480" "640x350"
#       EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x48 0" "640x350"
        EndSubSection

As you can see I only use Display 24 and my default is 1024x768. Gnome kept tossing me back into 1280x1024 until I uncommented the rest out. Modify your own xorg.conf to your desire.

D

---

### Post by ultima2k on 2005-05-05
The last one didn't work either.
And isn't the modeline generator only for warty? :S

---

### Post by Tsjoklat on 2005-05-05
[QUOTE=ultima2k]The last one didn't work either.
And isn't the modeline generator only for warty? :S[/QUOTE]

Hamana? Modeline what? I don't follow distro generated conf files, I edit them myself. But ahum, I am out of ideas then if it didn't work for you. Hopefully you'll find your answer somehow,

D

---

