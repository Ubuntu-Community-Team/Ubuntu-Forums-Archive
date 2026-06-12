---
title: "how can i get my screeen back to normal"
date: 2009-02-15
forum: General Help
---

### Post by cmay on 2009-02-15
hi.
i attached a screen shot of what happen when i rebooted from a live cd. i cant get my screen looking normal again. how  do i fix this. 
any help would be great. 
thanks.

---

### Post by cmay on 2009-02-15
fixed.
the solution was to remove all panels so that i could click apply on the not resizable window that handles the screen resultion after setting all font to size 6. i was merely pondering how it can be that livecd can change the resultion on ubuntu ,the first time i rebooted there  was something way wrong with screen as it was looking lind of dusty and grey and second time i logged in it was a wrong resultion. thats strange. why does this happen after running a livecd. that looked ok by the way.

---

### Post by cmay on 2009-02-16
actually not fixed. it does the same every single time i log in again. i cant make it stop. the above fix is the way to make it go away for on session but it startover again from the next time i start up the laptop.

---

### Post by anaconda on 2009-02-16
> **cmay said:**
> fixed.
the solution was to remove all panels so that i could click apply on the not resizable window that handles the screen resultion after setting all font to size 6. 

Did you know that you can move a window by pressing Alt and left button of your mouse...
So you can easily move the window so that you get the "apply" button visible..


If you have Nvidia graphics card you can propably fix your problem with "nvidia-settings"

It souds that your default resolution has changes to a too small one. You could try editing /etc/X11/xorg.conf file for setting the default resolution..

---

### Post by cmay on 2009-02-16
hi. 
i think i fixed it now. what i did was the xscreensaver session properties i turned of the screensaver and restatered the deamon. i noticed that ther was a message when i logged in about a deamon not running and i think i found the course. the xsettings deamon or what ever was for some reason not able to start. the last four times i been starting up the computer it has been acting normal.  i also found some other treads about this "xsettings deamon ot being able to start some settings may not work cerrect message." 
i cant remember the exact wording of it. 

thanks anyway. i hope i got it fixed now.

---

