---
title: "Edgy, Xorg, gdm startup issue"
date: 2007-02-04
forum: Desktop Environments
---

### Post by Suthern on 2007-02-04
I'm new to Ubuntu, but have been using linux (Suse 8,9,10) for a couple years as a secondary OS.
I started with a fresh install, then fooled around with beryl, xgl, and fglrx. It got so that  the boot proccess 'hung' at the 'UBUNTU' loading screen with the progress bar almost all the way to the right.

So, I rebooted in recovery mode and did apt-get remove xorg xsession-xorg xsession-xgl fglrx beryl bery-manager  emerald
Everything uninstalled nicely.

I then rebooted and it still hung at the same spot (I wanted to see if it would be nice and dump to to a console, or just leave me hanging. It choose the latter).

So, recover mode -> apt-get install xorg xserver-xorg. {enter}
then 'startx' and viola! I'm back in the regular ubuntu desktop. (except as root, not my normal user)

However, when I reboot normally, the display still hangs at the 'Ubuntu [======-]' loading screen.

recap: startx (from recovery console) works fine, but the normal boot hangs RIGHT before it would normally have me type in my name or choose a session type.  I would like to know how to reset the normal boot procedure to match that of startx.

(on a side note, booting from the install cd works fine as well)
Where would you recommend I start looking for what needs to be changed? I'm not afraid to muck around in files. ;-)

Thanks,
-Suthern

Videocard is a Radeon x800 GTO.

---

### Post by Clone5 on 2007-02-04
I've just started getting something similar, too. After I installed a new libgtk, whenever I started the computer it stopped at that 99% mark.  It does seem however, that the login manager still starts because the text cursor appears when I mouse over the text boxes and I can login if I enter my password.  However, no matter what I do I can not remove the image of usplash.  Unlike the OP, the same occurs when starting from the console it seems.

But whatever the problem may be, it seems to me to be linked to that latest gtk update.  It was working perfectly before, then update -> not working.

   libgtk2.0-0 (2.10.6-0ubuntu3 => 2.10.6-0ubuntu3.1)
   libgtk2.0-bin (2.10.6-0ubuntu3 => 2.10.6-0ubuntu3.1)
   libgtk2.0-common (2.10.6-0ubuntu3 => 2.10.6-0ubuntu3.1)

UPDATE:
I've tried rolling them back to the previous version, but my problem still remains.  So either the downgrade failed (I can't see anything I'm doing so that's a possibility) or I'm just prejudiced to that one upgrade and something else is the matter.

---

### Post by Suthern on 2007-02-04
Update: I've solved the issue!!! For anyone else with this issue, boot into recovery mode and check the gdm log files in /var/log/gdm.

I found out that GDM was still trying to launch fglrx, even after it was uninstalled. So I did 'vi /etc/gdm/gdm.conf-custom' and commented out the custom XGL and fglrx lines. did ':wq' then reboot, and boom, it works!

-Suthern

---

