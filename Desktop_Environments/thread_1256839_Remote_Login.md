---
title: "Remote Login"
date: 2009-09-03
forum: Desktop Environments
---

### Post by Wosco on 2009-09-03
Hi All

I Ubuntu under Login Preferences > Remote - I have mistakenly switched from "Remote Login Disabled" to "same as local".  Logged out to access Root login and now I have just a black screen no login or desktop.

Can anyone help please

Thanks
Ross

---

### Post by stefangr1 on 2009-09-03
Enabling remote login should not result in this kind of problems. Are you sure you didn't change anything else?

---

### Post by wojox on 2009-09-03
Hello, try and boot a liveCD and open you file browser, mount your drive and change it back.

---

### Post by stefangr1 on 2009-09-03
It seems like some gdm trouble. Do you get a cursor or not?

If you press Ctrl+Alt+F1, do you get a terminal where you can login?

If so, you can login and execute:
sudo dpkg-reconfigure xserver-xorg

---

### Post by Wosco on 2009-09-03
Thanks both for responding, I only changed Security > Allow System Administrator login....

I did try to reboot wit hte cd but now cannot access the bios boot options..  It all happens at once :(

Sorry no ctl alt f1 no change at all

---

### Post by Wosco on 2009-09-03
Thanks Guy's

For some reason bios option to boot from cd would not work now it does, I have the drive mounted how do I change this setting back?

---

### Post by wojox on 2009-09-03
Redo what you did that got you there in the first place.

---

### Post by Wosco on 2009-09-03
Sorry should explain that I have booted from live cd, how do I mount the system and change settings

---

