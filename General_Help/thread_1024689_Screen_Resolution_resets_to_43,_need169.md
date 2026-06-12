---
title: "Screen Resolution resets to 4:3, need16:9"
date: 2008-12-29
forum: General Help
---

### Post by jaredtrobinson on 2008-12-29
I bow to all you who are smarter than mwah. ;)

Flattery over.  Hello. I need help.  Ubuntu 8.10. New 26in 720p LCD.  Booting up Ubuntu goes into a 4:3 resolution of 1152x720 (something like that. not exactly sure. can get if needed) So I hook up my CRT monitor to it, change to 1360x768 and hook back up the LCD. All fine and dandy.  Reboot. Goes back to 1152x720.  Unsupported by my LCD.  So back to monitor to change resolution then back to LCD. Pain. Help?

How do I make Ubuntu keep the 1360x768 resolution no matter what? Through reboots and turn offs?

---

### Post by eBoxNet on 2008-12-29
Check this,it may help you

[http://ubuntuforums.org/showthread.php?t=1024252](http://ubuntuforums.org/showthread.php?t=1024252)

---

### Post by jaredtrobinson on 2008-12-29
Wow must be a lot of new TVs for Xmas. I see a couple of threads about this. Well I tried that link but didn't work.  Did same thing after restart of CTRL+ALT+BACKSPACE

If the monitor is plugged in the resolution will stay put at 1360x768.  So w/ monitor it is good, but w/ TV it goes to 1152x864 on boot up.

---

### Post by eBoxNet on 2008-12-29
did you reconfigure with tv pluged in?

---

### Post by jaredtrobinson on 2008-12-29
yes

---

### Post by eBoxNet on 2008-12-29
i just noticed...are you use HDMI ?

---

### Post by jaredtrobinson on 2008-12-29
no. VGA cable

---

### Post by eBoxNet on 2008-12-29
try adding theese to your xorf.conf on the DEVICE section :

Option "UseEDID" "False"
Option "PanelSize" "1200x800" <- change this to your resolution

---

### Post by jaredtrobinson on 2008-12-30
That didnt work.

What I have tried:

I created a file /etc/init.d/tvres.sh
> 
#! /bin/sh
# /etc/init.d/tvres.sh
#

	xradr -s 3

Ran through terminal:
> 
chmod 755 /etc/init.d/tvres.sh
update-rc.d tvres.sh defaults


This didn't work. Maybe I did it wrong? 

OK. looking at this I put xradr instead of xrandr. So i edited the file to make it say xrandr now but still doesn't work.

Here is file now:
> 
#! /bin/sh
# /etc/init.d/tvres.sh
#

	xradr -s 3


---

