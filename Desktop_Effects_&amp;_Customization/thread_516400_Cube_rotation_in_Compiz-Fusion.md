---
title: "Cube rotation in Compiz-Fusion"
date: 2007-08-03
forum: Desktop Effects &amp; Customization
---

### Post by PaulFXH on 2007-08-03
I just installed Compiz-Fusion using Vorian's [guide]("http://ubuntuforums.org/showthread.php?t=481314") and everything went well.
But, although the cube (actually it was a 2D sheet) rotated fine, I had no window decorations.
So, still following the guide, I installed Beryl/Emerald and got the window decorations.
But, the cube now only rotates when I choose Beryl as the window manager. With Compiz selected as WM, I have the decorations but cube doesn't rotate. Not only that but I can't do the fire-writing thing either.
And, yes, I have selected Desktop Cube and Rotate Cube in the CompizConfigSettingsManager.

One possibility is that my graphics card (nVidia GeForce4 MX 420) is a little long-in-the-tooth for Compiz-Fusion although it works perfectly with Beryl.
I'm hoping somebody will tell me I forgot something simple and my card is fine.
Anybody?

Thanks
Paul

---

### Post by atomkarinca on 2007-08-03
i had the same problem. i completely removed compiz, desktop effects, beryl and compiz fusion then i installed it using this guide [http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

now i have everything working perfectly.

---

### Post by PaulFXH on 2007-08-03
Thanks for the reply.
I did exactly what you suggested and ran the script (after correcting the typo in the run command) and everything seemed to install fine (no errors). Also, I downloaded everything that was offered.
Then I made the changes in System>Preferences>Sessions and rebooted.
But, no composite manager started.
Then I tried 
```
fusion-icon
```
in a terminal and got this error
```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!

```
Note that there is an entry called Compiz Fusion Icon in Applications>System Tools. Also, in System>Preferences these is another entry called CompizConfig Settings Manager.
However, neither of these two actually do anything when clicked.
Any idea what went wrong?

---

### Post by atomkarinca on 2007-08-03
[http://ubuntuforums.org/showthread.php?p=3083060&highlight=Error%3A+All+interfaces+failed%2C+aborting#post3083060](http://ubuntuforums.org/showthread.php?p=3083060&highlight=Error%3A+All+interfaces+failed%2C+aborting#post3083060)

---

### Post by PaulFXH on 2007-08-03
@atomkarinca
Thanks for pointing me to that thread. What that seemed to be saying was that you must NOT run the CF installer from the same directory in which it is installed.
Now that IS strange -- and it is what I had done (donwloaded to Desktop then navigated in terminal to Desktop and ran it.
Anyway, I was just about to uninstall all of the Compiz-Fusion stuff from Synaptic to try the install again when I noticed that nearly ALL of the compiz/compiz-fusion packages were not actually installed.
This is even stranger as it definitely said they were being installed while the installer was running.
So, I installed as much as I could from Synaptic and tried CF again (Note that some packages just wouldn't install -- such as compiz-extra and compiz-gtk (I use Gnome).
Anyway, after installing this stuff, CF actually worked -- more or less. So, the cube rotates and looks good but windows have no borders or buttons and are not wobbly.
So, unless anybody can suggest a quick fix, I'll probably uninstall everything and re-install from a directory OTHER THAN the one to which I downloaded the installer script.

---

### Post by PaulFXH on 2007-08-03
Actually, just after I posted the last post, I noticed that the Select Window Decorator option uses GTK Window Decorator as its default. When I changed this to Emerald, I got the borders and wobbly windows.
So nearly everything looks good now. Thanks a lot for your guidance.
Just one other thing -- does CF not have something equivalent to the Beryl Skydome?

Paul

---

### Post by atomkarinca on 2007-08-03
right-click the compiz fusion icon and select settings manager or system > preferences > compizconfig settings manager. under desktop cube > appearance tab > skydome > check skydome option. that should be about it.

---

### Post by PaulFXH on 2007-08-03
Now that's what I call a Desktop.
Thank you very much
Paul

---

