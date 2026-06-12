---
title: "Gnome keeps restarting after logging in"
date: 2009-02-04
forum: General Help
---

### Post by GrooveTherapy on 2009-02-04
So in the midst of getting my tablet working, I've hit this strange bug in intrepid.  Whenever I log in, my gnome panels keep restarting every 5 seconds and playing the startup sound.  It seems like multiple instances of my user are created...
I was editing the xorg configuration and rebooted before the problem occurred.  I could post the contents of my xorg if needed.  

If this is a bug with gnome, I'm not adverse to reinstalling, but I need some direction before trying this avenue.

What should I do??  Any help would be appreciated

---

### Post by adult swim on 2009-02-04
try resetting your xorg.conf by booting into recovery mode, going to a root shell and entering in ```
dpkg-reconfigure -phigh xserver-xorg
```
on second thought, i think if you choose xfix in recovery mode, it basically does the same thing i said above.

---

### Post by GrooveTherapy on 2009-02-04
Thanks for the quick response.  I tried both of your suggestions and they did essentially the same thing as you said.  My xorg.conf file has defaulted back to what it was when I did a fresh install, however the same problem still remains.

---

### Post by adult swim on 2009-02-04
did the problem occur before you first edited your xorg.conf?

---

### Post by GrooveTherapy on 2009-02-04
No, it did not.  I edited my xorg.conf to get my tablet working, which it did for about a day.  When I came back the next day, it stopped working, so I tried remaking the driver, modprobing it and rebooting, which caused it to work again.  After a few more reboots (and trying to use the tablet functionality at the login screen) the problem I have now begun.

---

### Post by adult swim on 2009-02-04
well that is a bummer!  dont worry about your custom xorg.conf, a backup should have been made of your old one in /etc/X11.  even though the panel is restarting, try manually restarting it by hitting alt+f2 and entering in ```
killall gnome-panel
``` and maybe that will get a hold on things.

---

### Post by GrooveTherapy on 2009-02-04
Well, the killall command will nerf the current panels, but it wont stop others from popping up/the startup sound playing.  I've just noticed now that my graphics display driver isn't loading either, if that hints at the problem at all.



And some on the fly developments: I just recieved a slew of errors asking me to delete some applets from my tool bar.  I said don't delete for all of them and the problem has stopped....strangely.  I'm going to reboot and see if the problem persists.

---

### Post by GrooveTherapy on 2009-02-04
Ah, no luck, the problems still remains.  Is this an issue with gnome or the login process?

---

### Post by adult swim on 2009-02-04
it seems like it is a problem with gnome.  unfortunately, i dont know what else to try here.  maybe someone will come along with some gnome-know-how.

---

### Post by GrooveTherapy on 2009-02-05
Bump.

Gnome only seems to restart infinitely when logging into my account - if I sign on as a guest, it only starts once. :confused:

---

### Post by GrooveTherapy on 2009-02-05
Bump

Ive tried reinstalling gnome via the console (ctrl alt f1) and using sudo apt-get install --reinstall gnome-desktop, but no good.

I've also tried deleting the gnome configuration files I could find (.gnome2, .gconf, .gconfd) which also did nothing.


Im starting to think this isnt a gnome issue...what else can I do?

---

