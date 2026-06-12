---
title: "startx -- x server Difficulties"
date: 2006-08-19
forum: Desktop Environments
---

### Post by Samurai Cal on 2006-08-19
Whenever I restart ubuntu, a blue screen appears with crazy writing around it that says something along the lines of "there was a problem starting your x server, it is now disabled.  re-enable it when you have repaired it".  So i run "sudo dpkg reconfigure-xserver xorg" and then go through that pointless blue screen process which seemingly should set everything back to normal.  But once that is completed, it is still just in terminal saying "cal@cal-desktop:~$" and waiting for me to type something.  It only works when I type "startx", and then everything starts up and works well for the most part.  The only thing that doesnt work, and i dont understand why, is when i press the power icon in the top right to turn off the computer, all that shows up is "log out", "lock screen", "switch user", and "hibernate"; there is no "shut down" or "restart".  And even if i click "hibernate", it basically just logs me off.

I think this problem originated when i was ******* with the xorg file (/etc/X11/xorg.conf), but i saved a backup before i started changing things and i replaced it, but it didnt change anything...

I just want to know how I can fix this whole thing, thanks.

---

### Post by Dr. Nick on 2006-08-19
Do you have to reconfigure every reboot? I am not totally sure what could be causing your error, what i can tell you though is why you have no shutdown, restart

When all is working as it should you will have gdm or kdm (if using kubuntu) running all the time, gdm is the first graphical thing to load up and it logs you on. When it is not running then you can not use the shutdown or restart actions as they are controlled by gdm, the startx command will bypass gdm thus the options dont work

---

