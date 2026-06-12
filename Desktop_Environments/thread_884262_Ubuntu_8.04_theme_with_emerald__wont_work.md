---
title: "Ubuntu 8.04 theme with emerald  wont work"
date: 2008-08-08
forum: Desktop Environments
---

### Post by Millie da kidd on 2008-08-08
Ok i installed emerald on ubuntu 8.04.
I also installed some themes.When i open emerald i see them.
I have installed compiz fusion.
On compiz fusion i switch the windows decorator from gtk windows decorator to emerald.Now I click on a them on emerald and nothing happens.What do i do?
Thank you in advance.

---

### Post by Tankerdog2002 on 2008-08-09
HOW TO USE EMERALD THEMES WITH COMPIZ IN 8 STEPS

Hi Millie da Kidd,

You mentioned GTK. Do you have all the dependents for GTK composition? Please make sure. I have noticed that even though Beryl/Compiz have merged, they still share some common ground.

I have installed Ubuntu 8.04 with Compiz/Emerald on about 23 machines in the last couple of months. (Dell, HP, Acer, MALIBAL-Satori-series, and even older xeon workstations.) We had no trouble with any of them by following the instructions below. 

1.) Make sure that you have everything you need for Compiz and Emerald before you begin; see attached screenshot of Adept Package Manager. Use any package manager you're comfortable with but make sure you have these packages installed.

[ATTACH]80791[/ATTACH]

2.) Then go to System > Preferences > Advanced Desktop Effects Settings, right click and choose; "Add This Launcher to Panel" (Now you don't have to go digging around for it anymore.)

[ATTACH]80792[/ATTACH]

3.) Open the Advanced Desktop Settings and scroll down to "Window Decorator" 

[ATTACH]80793[/ATTACH]

4.) Double click on the "Window Decorator" icon and type "emerald --replace" into the Command window-box. (Just remove whatever was there before.) Close window.

[ATTACH]80794[/ATTACH]

5.) Now ... go to: Applications > System Tools > Compiz Fusion Icon.
Dbl-click the icon. You will now have a little blue 'Compiz Fusion' icon in your panel by your clock.

[ATTACH]80795[/ATTACH]

6.) Right click the Compiz Fusion Icon thats now in your panel by your clock and do two things:
      __a. Reload Window Manager
      __b. Select Window Decorator and choose Emerald.

7.) Open terminal and type the command: sudo emerald --replace

8.) Re-boot

You're done.

Other toys: You can drag and drop your Emerald icon from System Administration into "Kiba-Dock" as I have done here and it will be easy to get to and change your themes. 

You can get Kiba-Dock for Debian here:
[http://swik.net/kiba-dock](http://swik.net/kiba-dock)

Just download Kiba-Dock to your desktop and click it...Debi-Installer will do the rest.



Cheers,
Tank

---

### Post by kholmvik on 2008-08-09
Hi!  seems like emarald wont load by default.

Try this:
install the fusion-icon:
sudo apt-get install fusion-icon

Start the icon by pressing "Applications" --> "System Tools" --> 
"Compiz Fusion Icon"

Right click on the icon that appeared in 'top panel'
"Select Windows Decorator" --> "Emarald"

Restart compiz (CTRL - ALT - Backspace)


Hopefully you should now be able to switch themes with emarald manager.:-({|=

---

### Post by Tankerdog2002 on 2008-08-09
Open terminal and type:

sudo emerald --replace

Then reboot.

---

### Post by dodle on 2008-09-12
Thanks Tankerdog, worked perfectly.

---

### Post by dseybert on 2008-09-13
edit

---

### Post by EnGorDiaz on 2008-09-13
install ccsm compiz fusion icon emerald theme manager check all your compiz dependancies emerald workd with both beryl and compiz also

---

### Post by SSanders on 2008-09-13
Hi everyone,

I have been at this same problem for two days and yet to get it working.

Another problem I get is when I set Visual Effects in Appearance Preferences to Normal or Extra my 'window borders' disappear so I cannot tell if the theme is working or not.

If I set the Visual Effects to none the theme does not change at all. I did notice in Terminal when I had typed 'emerald --replace' that 'Reloading...' would appear if I clicked a new theme in the Emerald Theme Manager but nothing happens.

I have looked at many threads and followed similar instructions but to no avail.

EDIT: I have all the compiz packages and dependencies installed.
Using both Ubuntu Hardy Heron 8.04 and Ultimate Edition 1.9

---

### Post by TheUbGuy on 2008-09-13
> **SSanders said:**
> 
If I set the Visual Effects to none the theme does not change at all. I did notice in Terminal when I had typed 'emerald --replace' that 'Reloading...' would appear if I clicked a new theme in the Emerald Theme Manager but nothing happens.


If you set the Visual Effects to none, then Emerald will of course not work - you need to have desktop effects (i.e. Compiz)  enabled - check 'Extra' under Visual effects. 

Getting Emerald to work (and be enabled every time you boot) is fairly straight-forward. Do you have the Compiz Config Settings Manager? It would be under System->Preferences->Advanced Desktop Effects Settings? If not, go to Synaptic Package Manager under System->Administration and do a search for compizconfig. You should find compizconfig-settings-manager. Install it and then you will have it under Preferences->Advanced Desktop Effects Settings. Go to Effects->Windows Decoration. Under Command, enter: emerald --replace and then reboot. You should now have Emerald running.

---

### Post by SSanders on 2008-09-14
The visual effects work how they should and are fun to mess with.

BUT, I still dont get the theme changes for some reason as "my 'window borders' disappear when I set Visual Effects to Normal or Extra so I cannot tell if the theme is working or not." I suppose this is my issue, NO window borders NO theme.

I have tried all the settings suggested in many threads where others have had similar problems that were mostly solved.

As I said in my previous post, ALL compiz packages and dependancies are installed. Even Compiz Fuzion is installed.

In compiz fuzion the window manager is Compiz and the decorator is Emerald. With Visual effects set to None and then clicking Reload Window Manager in Compiz, my screen resets and all the 'window borders' vanish. Checking the Visual Effects window shows it setting is now Extra.

I have tried the above suggestion and also setting 'emerald --replace' in 

System > Preference > Window Decoration > Command

Then replace

/usr/bin/compiz-decorator

to

/usr/bin/emerald --replace

as well as setting '/usr/bin/emerald' in the same place.
Also tried, 
sudo gedit /usr/bin/compiz-decorator

Changed line 30 from 

USE_EMERALD="no"

to

USE_EMERALD="yes"

Tried ALT+F2 with emerald --replace.

Seems I am caught in a catch 22. :(

Oh and my system is
1Ghz P3 Coppermine, 640mb ram, 40gig hdd ,Asus GeForce4 MX 440 AGP8x Dual head.

---

### Post by Tankerdog2002 on 2008-09-15
Hmmmmm....dual monitors always seem to be a challenge for all of us.

Sanders... by any chance do you have xserver-xgl installed? 

Are you running Xinerama, if so, are you using the X C binding or the X11?

And, have you tried x2VNC (dual screen hack) by any chance?

All of these are factors when using Emerald on a dual-head rig.

Our geeks have to experiment and tweak things to get dual-head set ups working at the office. They're like pampered cats ... they're very finicky.

Oh ... one other thing ... I'm sure you already have this but just in case, do you have your Nvidia-settings installed?

---

