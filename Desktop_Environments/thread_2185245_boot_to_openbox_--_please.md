---
title: "boot to openbox -- please"
date: 2013-11-01
forum: Desktop Environments
---

### Post by ersatzsplatt on 2013-11-01
I've looked at a few webpages, like:
[http://ubuntuforums.org/showthread.php?t=75471](http://ubuntuforums.org/showthread.php?t=75471)
and
[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)

It looks like I only need to type:
sudo apt-get install openbox obconf

and

openbox --replace

but when I do that, it still boots to the same old Metacity


What do I have to do to get my Ubuntu 12.04.3 LTS  32 bit system (3.8.0-32-generic) to run openbox instead of metacity?

I don't see an option to run openbox when I boot.

BTW, when I run 
openbox --replace
I see:
Openbox-Message: Failed to open the display from the DISPLAY environment variable.

---

### Post by Frogs Hair on 2013-11-01
I have installed Open Box along with LXDE and you have select the session at login  from the menu next to password input box. One of your links goes back to 2005 and is referring to Gnome 2 and no longer applies.

---

### Post by ersatzsplatt on 2013-11-01
I don't get any login menu.  It boots directly into Metacity.  I know I'm not doing something right.  I'd be happy to lose the Metacity option altogether.  Any specific suggestions?

---

### Post by ersatzsplatt on 2013-11-01
O.k., now things have changed.  I tried reboot a few times and it always booted to Metacity.  Now I tried turning the system off and then powercycling before turning it on.  Now when I boot, the system goes through the normal BIOS boot screen, then goes to ubuntu dark purple black, then the screen that has "ubuntu" with 5 orange dots beneath it.  ... and stays there.  The system is running, I know, because I can ssh in.  But I can't get to virtual terminals from the system keyboard. It just stays at the 5 orange dots screen.
I had taken one other step, not noted above.  I added the file ~/.xinitrc with contents: exec openbox-session
Any suggestions?

---

### Post by Frogs Hair on 2013-11-01
Prior to installing Open Box what desktop were you using , Unity or Classic ?


Edit: I installed open box from synaptic and it appeared in the login list and I am currently typing from Chrome in Open Box . There are two sessions offered Open Box and Open Box Gnome.

---

### Post by ersatzsplatt on 2013-11-01
Hey Frogs -- thanks for the thoughts.
I installed unity, I'm thinking.   The standard. 12.04 desktop.
Key for me was apt-get remove lightdm; reboot There was some kind of contention where lightdm started and so openbox was not starting so sweet.

---

