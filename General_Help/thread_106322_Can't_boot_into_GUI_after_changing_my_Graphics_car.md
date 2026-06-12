---
title: "Can't boot into GUI after changing my Graphics card"
date: 2005-12-20
forum: General Help
---

### Post by slypie on 2005-12-20
Hi all, first off got to say Ubuntu is the easiest Linux Distro I've used (Enough arse kissing) I am a Linux noob so bear with me.  I installed Ubuntu on an old PC with onboard graphics.  I decided to install a PCI NVidia MX440 card to free up the RAM a little.  After doing so it won't boot into the GUI (Gnome) and comes up with a blue screen with the following message-

"Failed to start the X server (Your Graphical Interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?" 

I press yes and it comes up with info which I click through and then comes up with a message saying- 

"The X server is now disabled.  Restart GDM when it is configured correctly."

Then it goes to a prompt for the username and password.

I am totaly lost on how to fix this.  I'm assuming that it's because it can't find the drivers for my new card.  Can anyone help me to fix this problem.

Thanks in advance...:)

---

### Post by Shinkan on 2005-12-20
You're probably right, Xorg tries to start your old driver for your new card ... not so good : )

Try to log with your username.

Then try :

> sudo nano /etc/X11/xorg.conf

Find this section :

> Section "Device"
    Identifier   "GeForce FX"
    Driver       "whatever"
    ...
EndSection

Replace whatever with "vesa".
Push Ctrl + X to quit, answer Y (yes) to save, then reboot gdm.

> sudo /etc/init.d/gdm restart

switch to Ctrl + Alt + F7 to go back to graphical mode, or just reboot : )
You can repeat these steps with "nv" driver, which is surely better for your card (3d accel ?).

---

### Post by slypie on 2005-12-20
Shinkan, cheers for the quick reply but when I go to edit sudo nano /etc/X11/xorg.conf the screen is blank.  Any Ideas?

---

### Post by SickTwist on 2005-12-20
Are you sure that you're spelling it correctly? Also, Linux is case sensitive so be sure to use an uppercase X in X11.

---

### Post by DocFox on 2005-12-20
Try:

 ```
sudo dexconf -o /etc/X11/newxconf
```

This will generate a rudimentary xorg.conf file which you can check out. Under [FONT="Courier New"]Section "Device"[/FONT] you should see something that looks appropriate for your graphics card.

Then backup the old xorg.conf (just incase) and copy newxconf ontop :

```
sudo cp xorg.conf xorg.conf.bak
sudo cp newxconf xorg.conf

```

Let me know if it solves your problem.

---

### Post by DocFox on 2005-12-20
You will, of course, need to be in /etc/X11 when you do the file copying.

And then you'll have all the fun of setting up the NVIDIA driver...](*,)

---

