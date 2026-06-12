---
title: "System Beep on Logout."
date: 2009-03-25
forum: General Help
---

### Post by AbsentHarvest on 2009-03-25
I have a customized sound theme for my Ubuntu 8.10 System.
Well, even on default sound on Logout I still get a System Beep sound for Logging out instead of Default or my Custom sound.  This is the only defect, All the other sounds work perfectly and Sound in general is great.  It's just the System Beep when I log out, it bugs me.

I've tried various ways...

I've edtied the...
sudo gedit /etc/gdm/PostSession/Default

And added...
/usr/bin/canberra-gtk-play --id=”desktop-logout”

Before...
exit 0

I have also tried adding...
/usr/bin/canberra-gtk-play --id=”desktop-logout” --description=”GNOME Logout”
In the same spot as the other command.  Neither one seems to work.

Any Suggestions????? :popcorn::popcorn:

---

### Post by Denestria on 2009-03-25
Disabling the system beep

> You can disable this by editing a file and entering two simple lines.

gedit /etc/modprobe.d/blacklist

And then add:

#silly speaker beep
blacklist pcspkr

Save your file and the speaker beep will be gone when you reboot.

If you don’t want to wait until a reboot, simply type:

sudo rmmod pcspkr

[http://www.arsgeek.com/2006/08/23/how-to-turn-off-the-annoying-system-beep-in-linux-debianubuntu/](http://www.arsgeek.com/2006/08/23/how-to-turn-off-the-annoying-system-beep-in-linux-debianubuntu/)

---

### Post by AbsentHarvest on 2009-03-26
This worked.  Thank you.

---

### Post by khelben1979 on 2009-03-26
In Kmix you can adjust the volume of beep graphically, too.

---

### Post by rcbinwi on 2009-08-05
I have a newbie question for this.  I followed the above instructions and got the result:
> Could not save the file /etc/modprobe.d/blacklist.
You do not have the permissions necessary to save the file. 
Please check that you typed the location correctly and try again.

Any suggestions?

---

### Post by Lampi on 2009-08-05
```
sudo gedit /etc/modprobe.d/blacklist
```
... will give you the necessary rights to edit this file

---

### Post by philinux on 2009-08-05
That should be gksudo ^^^

---

### Post by rcbinwi on 2009-08-06
Got it!  No more beep.

This seems to turn the speaker off altogether.  However, I was wondering: is there a way to get the speaker not to beep when the computer turns off, but get it to beep when, say, the battery is critically low?

---

