---
title: "Custom resolution doesn't stick!"
date: 2010-01-11
forum: Desktop Environments
---

### Post by ripeart on 2010-01-11
Hi,

I'm having an issue with a fresh install of 9.10 Desktop and a monitor which has a native res of 1360x768. I've issued the following commands in a terminal session which work as expected:
[FONT=Courier New]
xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync

xrandr --output VGA1 --mode 1360x768[/FONT]

Then upon a suggestion in another thread, I added the above xrandr commands to '/etc/gdm/Init/Default' just before the following command:
[FONT=Courier New]
initctl -q emit login-session-start DISPLAY_MANAGER=gdm[/FONT]

So the final looks like this:

[FONT=Courier New]xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
xrandr --output VGA1 --mode 1360x768[/FONT]
[FONT=Courier New]initctl -q emit login-session-start DISPLAY_MANAGER=gdm[/FONT]

Rebooted to 1024 x 768. Checked in display control panel and didn't see my custom resolution. Next, I created a startup script with the above xrandr commands then performed the following commands on the file, where 'resolution' is the name of the file.

[FONT=Courier New]update-rc.d resolution defaults
chmod +x resolution[/FONT]

Rebooted to 1024 x 768, and no custom res in my display prefs. Anyone have any idea where to go from here? It works when I do it manually, however that's a bit inconvenient and I would like to apply these settings upon boot. Any ideas?

Thanks.

---

### Post by Lorin Ricker on 2010-01-12
See this thread: [ **"Unknown Monitor" and cant increase resolution beyoud 800x600**]("http://ubuntuforums.org/showthread.php?t=1364460")

See especially Post #14 on your problem.  Hope this helps!  -- Lorin

---

### Post by ripeart on 2010-01-12
I appreciate your help however I have scrapped the install and moved to a different machine. Resolution works fine on this one!;)

---

