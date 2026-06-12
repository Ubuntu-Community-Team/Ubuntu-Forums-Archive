---
title: "Compiz Fusion problems. NO WINDOWS BORDERS"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by Tranks on 2007-08-29
Hey there,
I've installed compiz fusion on my machine, and it work for me for a few days, then it just screwed up.

1) There is NO CUDE
2) There aren't WINDOWS BORDERS
3) There aren't ANY EFFECTS

I've tried to do in Alt+F2 window "compiz --replace" or "emerald --replace" and it's stiil ******.


Can you guys PLEASE help me?:S

Thanks,
Trankz.

---

### Post by 505 on 2007-08-29
Open the Compiz settings window (in System > Preferences) and make sure the module 'Window decorations' is loaded. This should give you window border. To add the cube, first quit compiz (metacity --replace), set the number of desktops to 4, then start compiz again (using compiz --replace).
If you still don't have any effect, first check if all the plugins are loaded. Otherwise, run compiz from a command line and search for any error messages.

---

### Post by Tranks on 2007-08-29
I've loaded the Window Diraction and still aren't any window borders =\

How do i change the number of desktops from 1 to 4?


Thanks.

---

### Post by Hyperkill on 2007-08-29
I had the same problem as you before and this is how I fixed it.  I found out that it was a bad video card driver which was giving me a lot of display errors.  So, I went to this site ( [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ) created by tseliot and downloaded Envy.  I ran that and then rebooted my computer.  Then, I went into the Synaptic Package Manager located in System > Administration and did a search for compiz.  I then checked every package with a green box next to it and uninstalled them so I could start out fresh.  Then I went to this site : [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) and followed the guide completely and I now have a working version of Compiz after hours and hours of frustration.  Hope it helps and works for you as well!

---

### Post by £Xo7XEEQK38037M# on 2007-08-29
> **Hyperkill said:**
> I had the same problem as you before and this is how I fixed it.  I found out that it was a bad video card driver which was giving me a lot of display errors.  So, I went to this site ( [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ) created by tseliot and downloaded Envy.  I ran that and then rebooted my computer.  Then, I went into the Synaptic Package Manager located in System > Administration and did a search for compiz.  I then checked every package with a green box next to it and uninstalled them so I could start out fresh.  Then I went to this site : [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) and followed the guide completely and I now have a working version of Compiz after hours and hours of frustration.  Hope it helps and works for you as well!Followed the entire guide, but no borders. 

The borders have disappeared since the last couple of updates and it is annoying that this is still hard to config, as with a lot of other stuff under Ubuntu...

---

### Post by jhernandez1270 on 2007-08-29
have you tried changing your theme?  System-> Prferences -> Theme

choose the default theme for fiesty ( Human) see if that helps

---

### Post by jsully1 on 2007-08-29
You need to add two bits to your xorg.conf  - assuming you're using nVidia here is an example of the portion you'll want to edit

Section "Device"
    Identifier     "NVIDIA GeForce FX 5500"
    Driver         "nvidia"
    Option         "RenderAccel" "true"
EndSection

You need to add
Option "AddARGBGLXVisuals" "True"
Then restart X

---

### Post by juanlu on 2007-08-30
Have you made any recent update?

I have had troubles with compiz since last update, I can't make it work. More people is having the same troubles, but I haven't find any clear solution yet.

good luck!

---

### Post by £Xo7XEEQK38037M# on 2007-08-30
> **jhernandez1270 said:**
> have you tried changing your theme?  System-> Prferences -> Theme

choose the default theme for fiesty ( Human) see if that helpsDoesn't do the job...> **jsully1 said:**
> You need to add two bits to your xorg.conf  - assuming you're using nVidia here is an example of the portion you'll want to edit

Section "Device"
    Identifier     "NVIDIA GeForce FX 5500"
    Driver         "nvidia"
    Option         "RenderAccel" "true"
EndSection

You need to add
Option "AddARGBGLXVisuals" "True"
Then restart X
Options were already in there...



> **juanlu said:**
> Have you made any recent update?

I have had troubles with compiz since last update, I can't make it work. More people is having the same troubles, but I haven't find any clear solution yet.

good luck!Ever since one of the last updates it doesn't work anymore. In the configmanager I only have the option "flat file configuaration". As stated above I followed the guide, which advises to remove all compiz and then reinstalling it. 

It is too much trouble to get things working properly under Ubuntu (Linux in general). Everybody is so fired up about Ubuntu, but I'm still not too impressed seen all the configuration and editing of files I need to do in order to make something work.:| :neutral:

---

### Post by Jason.TJ.Johnson on 2008-01-02
> **jsully1 said:**
> You need to add two bits to your xorg.conf  - assuming you're using nVidia here is an example of the portion you'll want to edit

Section "Device"
    Identifier     "NVIDIA GeForce FX 5500"
    Driver         "nvidia"
    Option         "RenderAccel" "true"
EndSection

You need to add
Option "AddARGBGLXVisuals" "True"
Then restart X

Damn.
That worked for me.
Thanks!

For the record, my xorg.conf file doesn't have the RenderAccel line either, but I didn't add it.
nVidia GeForce 6800GT

---

