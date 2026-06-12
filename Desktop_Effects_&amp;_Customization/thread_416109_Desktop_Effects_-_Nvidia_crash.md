---
title: "Desktop Effects - Nvidia crash"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by johnnybgood115 on 2007-04-20
Hi all, 

I have just upgraded from Ubuntu 6.10 to 7.04.  I was looking around and checking everything out, trying to get my screen resolution to 1280x900 (for my widescreen display)  I stumbled upon the "desktop effects"  As I tried to enter the menu, it prompted me saying I had to install new drivers for my Nvidia Geforce 3 graphics card.  That's done, so it tells me to reboot.  Upon reboot, the "X server" crashes and it says that I cannot open the GUI interface. It then gives me a command prompt.  I am relatively new to linux and hoping that there is someway to reverse this update to my drivers or possibly erase them.  Also, how do I install the drivers for the Nvidia Geforce 3 graphics card and can i get widescreen resolution? 

Thanks!!!

---

### Post by mgmiller on 2007-04-22
Here is a quick way to get back to a gui desktop.  I assume after you get the "x is broken" screen, you end up with a blinking cursor that will accept keyboard input.  First, you need to change the video driver that loads:

```
sudo nano /etc/X11/xorg.conf
```
Enter your regular log in password when prompted.

Notice that the X in X11 is a capital X.

Next, scroll down using the down arrow key to the area that is headed   Section  "Device"
Under that should be an Identifer line showing your video card and then a line that says
Driver  "nvidia".  
Using the right and left arrow keys and the delete key, change "nvidia" to "nv"  You can just delete the idia and it will work fine.

Next, save the file by hitting ctrl and o.  (That is a lower case letter o) This will prompt you about writing the file.  Just hit enter to do it.  Then ctrl x to exit.

Finally, enter the command:
```
startx
```
and your gui should return.

You will now be back running the open source nv driver.  To try to get it to re detect your video card and monitor, use the command:

```
sudo apt-get install --reinstall xserver-xorg
```
This should force a re detect of everything.

It should give you the screen resolutions you want.  I have found that some nividia cards won't support some wide screen resolutions, so check to see if yours will do what you want.  If need be, you can manually edit your xorg.conf and add the resolution to the list on the 24 bit color depth line.

If you want to enable the desktop effects (still considered beta, so things may break or require tweaking), if using the  restricted drivers manager installed the wrong driver, then you may need to look in syaptic package manager.

In synaptic package manager, do a package search on nvidia-glx

I think your geforce 3 card may need the nvidia-glx-legacy instead of the nvidia-glx package.  If so, uninstall nvidia-glx and install nvidia-glx-legacy.  
Again, I am not totally sure which older cards are supported by which driver, so you may want to read up on this a bit before committing to it.

Finally, after installing the correct driver, use the command:
```
sudo nvidia-xconfig
```
to enable the driver.

Other commands that may prove useful that speed up rendering for the compiz 3d desktop are:

```
sudo nvidia-xconfig --composite 
sudo nvidia-xconfig --render-accel 
sudo nvidia-xconfig --allow-glx-with-composite 
sudo nvidia-xconfig --add-argb-glx-visuals
```

Hope this helps.

---

### Post by johnnybgood115 on 2007-04-22
Thanks a lot...i got my X running again, however, do you know how to install the nvidia-glx-legacy...are there repositories that need to be added b/c it does not appear in the synaptic manager and terminal gives me a "not available" message when i run..
```

sudo apt-get install nvidia-glx-legacy
```

---

### Post by mgmiller on 2007-04-22
I'm glad you got your x back.  I assume you did your homework on your video card as I suggested and you do really need the legacy package.   It is in the multiverse repository.  To turn on the extra repositories, run synaptic package manager and then click on Settings on the top of the window and then repositories.  The first tab is the Ubuntu Software tab, just put check marks next to the repo's you want.  I have all of them checked except Source code.  Then click close and you should be prompted to click the reload button in the upper left.  After that, your search for the nvidia-glx-legacy package should work.

Good Luck.

---

### Post by johnnybgood115 on 2007-04-23
Yeah I'm still getting errors even after installing the legacy drivers and enabling them.  The X server just really hates my graphics card :)  I've contacted Nvidia and they're trying to give me a hand now with the drivers on their website.  If you've got more advice that would be appreciated.  Otherwise, thanks for all the help you've given so far.  

-- John

---

### Post by mgmiller on 2007-04-23
You're welcome.  Glad I could help as much as I did.  Hopefully the good people at nvidia will be able to straighten out the rest of your problems..

---

