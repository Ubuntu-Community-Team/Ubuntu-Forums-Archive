---
title: "NO window controls?...HELP!"
date: 2010-03-08
forum: Desktop Environments
---

### Post by saabaru on 2010-03-08
I am fairly new to ubuntu. Been using for about 2 years now. I am running dual boot Ubuntu 9.10/windows 7. I can open a window (firefox for example), and it does not have the "minimize", "maximize", or "close" buttons. I also cannot move the windows. The only was to exit from it is to select it from the "file" dropdown. menu. If you could tell me how to fix this, it would be greatly appreciated! TIA

---

### Post by hhh on 2010-03-08
Are you running Compiz? Did you accidentally uncheck the "Windows Decoration" plugin under "Effects" in CCSM?

---

### Post by nilarimogard on 2010-03-08
Try pressing ALT + F2 and entering:
compiz --replace

If you disabled this accidentaly, go to System > Preferences > CompizConfig Settings Manager and make sure the "Window decoration" plugin is enabled.

If you could tell us if you're using Compiz w/ Emerald or not, we could be more specific :)

---

### Post by saabaru on 2010-03-09
Update....I rebooted, and most everything went back to normal. For whatever reason, in the effects menu (none,norm,extra) I select normal, it applies it, but then i go back into it, and it says none. i dont know enough about ubuntu to figure it out yet. Thanks for the help with the window issues!

*edit- I am running compiz and window decoration was still checked.

---

### Post by Sky Aisling on 2010-03-09
Hello Saabaru,

I too am new at using Linux Ubuntu and this forum.  However, I had the same situation occur yesterday on my system.   Please see my forum thread [http://ubuntuforums.org/showthread.php?t=1425312](http://ubuntuforums.org/showthread.php?t=1425312).

I recieved help by going to the Xfce website [http://www.xfce.org/](http://www.xfce.org/) (I use Xfce for my desktop. Which desktop do you use?).  The people there suggested that the windows manager wasn't running.  Here is the solution they offered and it's worked:

Go to Applications/Accessories/Terminal.  
Open a terminal window (if your windows will work enough to let you).
Type inthe words:**  xfwm4 --replace --daemon** 
Terminal is case sensitive, so make the words exact.
Give the system a moment to digest this.

Hope this helps.

---

### Post by chewearn on 2010-03-09
If you have nvidia, edit /etc/X11/xorg.conf
```
gksudo gedit /etc/X11/xorg.conf
```Add this line under Section "Screen"
```
Option "AddARGBGLXVisuals" "True"
```

Save the file, and reboot.

---

### Post by saabaru on 2010-03-09
Ok, windows buttons are fixed. Thank you! Now with concern going to the "effects". It will let me apply it, then I close the window, and go back into it, it is back on "none". Do i have to reboot after i modify the effects portion?

---

### Post by nilarimogard on 2010-03-09
You most probably need to enable the restricted drivers to use the effects. If you use Nvidia, see [here]("http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html"). If you have an ATI graphics card, go to the ATI website, download the linux driver (it should be a .run file), download it to your desktop and then run this in a terminal:
```

cd ~/Desktop
sudo chmod +x name_of_ati_drivers.run
sudo ./name_of_ati_drivers.run
```
Where name_of_ati_drivers.run is the name of the driver you've downloaded.

"sudo chmod +x" makes the file executable and the last command runs it. Then you need to restart your computer and you should then be able to enable the effects.

---

