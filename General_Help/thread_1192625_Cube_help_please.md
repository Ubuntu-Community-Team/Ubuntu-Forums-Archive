---
title: "Cube help please"
date: 2009-06-20
forum: General Help
---

### Post by owens5955 on 2009-06-20
Hello everyone!!

I am quite new to Ubuntu. I have installed Jaunty and all is well my next task was to use the cube. I followed all the advise that I saw and no cube yet. I installed CCSM enabled desktop cube and rotate cube set horizontal to 4 and all i get when pressing ctrl + alt + up is an Icon with desk 1 on it. have also set the number of desk tops to 4.
I have a Dell b130.
If anyone can help i would appreciate it..

Thanks,

The New Newbie :)
Jeff:lolflag:

---

### Post by VCoolio on 2009-06-20
Did you specify ctrl+alt+up as hotkey for that? I think default is ctrl+alt+left/right or ctrl+alt+left mouse key.

---

### Post by owens5955 on 2009-06-21
Yes,

I have that set.

---

### Post by Marlonsm on 2009-06-21
Do you have your video drivers working? Can you use any other effects, like Wobbly Windows, for example?

---

### Post by 3rdalbum on 2009-06-21
EDIT: After a bit more investigation I concur with Arand and Marlonsm: Compiz is not running, and Metacity is acting as the window manager. Check that you have 3D acceleration happening:

```
glxinfo | grep "rendering"
```

If it says "direct rendering: no" then you need to install a driver for your graphics card. If it says yes, then try starting Compiz manually:

```
compiz --replace
```

If there are any error messages, tell us. If Compiz starts properly, DON'T CLOSE THE TERMINAL, just log out and log back in again; and if Compiz isn't running then, press Alt-F2 and type that command in.

You are using Ubuntu Netbook Remix? If so, the netbook launcher interferes with Compiz (or at least, it used to in Intrepid and I assume it's the same in Jaunty). Either run the netbook launcher interface, or Compiz - not both.

-------inappropriate information for this question but might still be useful to someone reading the thread with a similar problem ------------
Set "Horizontal virtual size" to 4, and Vertical Virtual Size and Number of Desktops to 1. It's a bit counter-intuitive like that.

Don't get too hung up on the Compiz effects, there's a lot more to Linux than that.

---

### Post by Arand on 2009-06-21
> **Marlonsm said:**
> Do you have your video drivers working? Can you use any other effects, like Wobbly Windows, for example?

It sound as though this might be the crux.

Enter this command into a console window to find out how and whether Compiz is running:```
ps ax | grep compiz
```If you don't see a command starting with "compiz" or "compiz.real" in the output, then Compiz is failing to start altogether.

I that case you most probably have to get your video drivers up first.

- Arand

---

### Post by owens5955 on 2009-06-21
You guys are great!!!!

Manual start of Compiz did it !!

Thanks alot

---

### Post by ns_477 on 2009-12-03
ok so i have a something of a question then.

i have all the plugins for the cube running and all i get is a flat 2 sided picture that rotates back and forth, i tried the above command and  the response was "yes" to the rendering and ran the code for manual launch of compiz and received this error


Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x600) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!


i have checked for GLX and have run into the same issue when trying to intall it so my questions are these:
how do i uninstall/disable the netbook interface "human" whatever the crap and get GLX up for this to work? and secondly after i do this if i decide later that i want to go back will that be doable or not?

any help is greatly appreciated! thanks!

---

