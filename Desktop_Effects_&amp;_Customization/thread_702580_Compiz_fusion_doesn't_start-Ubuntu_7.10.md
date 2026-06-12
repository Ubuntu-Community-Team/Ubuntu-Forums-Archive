---
title: "Compiz fusion doesn't start-Ubuntu 7.10"
date: 2008-02-20
forum: Desktop Effects &amp; Customization
---

### Post by antonis9891 on 2008-02-20
Hi everybody. I installed compiz fusion in Ubuntu 7.10 Gutsy and when I press alt+F2 and type compiz --replace, nothing happens. I also installed manually the xserver-xgl. When I type the command at terminal, it returns:
Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Enabling Xgl with nVidia drivers...
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop
and when I close terminal, all the windows have no bar with close, minimize etc. I checked nvidia drivers are enabled and in use.
Thanks

---

### Post by akudewan on 2008-02-20
It seems you don't have 3D acceleration. Try running "glxgears" and see if you're getting an error.

---

### Post by antonis9891 on 2008-02-20
My card is 8600M GT so I think it supports 3D acceleration. I  opened terminal and ran glxgears, and appeared a window with 3 colourful rotating gears. I think it's normal. Also, the first time I ran compiz --replace there was a line Checking for Xgl: not present and Checking for nVidia: present but I'm not sure about nvidia line. Then I installed xserver-xgl and here's the problem

---

### Post by antonis9891 on 2008-02-21
Is there possibility that the drivers do not work properly? I think there is difference in the graphics when I play videos when I'm in linux and in windows.

---

### Post by akudewan on 2008-02-21
> **antonis9891 said:**
> Is there possibility that the drivers do not work properly? I think there is difference in the graphics when I play videos when I'm in linux and in windows.

If that was the case, then Compiz would be slow, but it would still work.

Your problem might be a simple case of some settings being incompatible, or something else. I really don't know. Maybe you could lookup some of the threads that are on ubuntuforums.

---

### Post by antonis9891 on 2008-02-24
I made a fresh install, installed the drivers, and when I typed compiz --replace, I got:
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0407 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
I read that nvidia doesn't need xgl, and I didn't install xserver-xgl because if I do that, I will get nvidia not present.

---

### Post by steveneddy on 2008-02-24
I think you should start Compiz by

[COLOR="Blue"]System --> Preferences --> Appearance 

On top of the window, navigate to the "Visual Effects" tab, click on it

Select the option that says "Extra" (or the level of your choice)[/COLOR]

That should start Compiz for you.

Compiz is defaulted to run natively in Gutsy.

Also look at your restricted drivers manager.

[COLOR="Blue"]System --> Administration --> Restricted Drivers Manager

enter your password

and make sure that the box is checked for your video card, if you have nVidia or ATI.[/COLOR]

[COLOR="Red"]Restart X ( Ctrl+Alt+Bksp )[/COLOR]

Log in and try and start Compiz again by going to 
[COLOR="Blue"]
System --> Preferences --> Appearance[/COLOR]

Hope this helps.

---

### Post by antonis9891 on 2008-02-24
Thanks. Now I have curved windows, I can paint with fire etc, but I don't have desktop cube.  I go custom set of effects and I enable desktop cube, log out and log in but again the cube does not appears.

---

### Post by Gazza-spins on 2008-02-24
Hey there dude. you need to enable "rotate cube" in the compizconfig settings pannel, once you've done that hit cntrl alt, and drag with your mouse.

Good luck

---

### Post by rohedin on 2008-02-24
If you start Compiz from the terminal, you can't close the terminal or else Compiz closes as well. Either just minimize the terminal or start compiz from a shortcut or icon or something.

EDIT: Whoops, too late, didn't read the whole topic :o

---

### Post by battleshipterry on 2008-02-24
This may help let us know. make sure you have four desktops on the bottom task bar any less cube will not work I think.cube needs 4 sides.

---

### Post by antonis9891 on 2008-02-25
Ok. Now I made it work all the way. I was fool because I thought that if I install and enabl cube with compiz --replace, then a cube will replace the desktop.
Thanks everybody.

---

### Post by ed3120 on 2008-02-25
I have MythBuntu 8.04 Alpha 2 with XFCE.  I have installed and enabled Compiz, but I don't see any effects.  I have the Advanced Desktop Effects Settings menu, and I've enabled effects, but I just don't see any effects.

I have set Compiz to start in my /etc/xdg/xfce4-session/xfce4-session.rc

I'm running the nVidia restricted drivers.

---

### Post by drubin on 2008-02-25
I was also having that issue, I played around a little now every time i try and use any command with compiz in it it logs me out of xserver

---

