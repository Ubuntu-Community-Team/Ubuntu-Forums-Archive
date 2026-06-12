---
title: "[SOLVED] Emerald and Compiz problem -- loosing title bar!"
date: 2008-12-29
forum: General Help
---

### Post by BreeZier on 2008-12-29
Hello there, couldn't find an answer around, so here i go :P

Using Ati latest drivers on a Radeon HD 4850, i'm trying to set my windows to look nice

typing
emerald --replace
in a terminal makes everything work -- nice borders and all
BUT, the terminal jumps a line and stays there, doing nothing. all i can do is write random stuff that doenst do anything or close the terminal.

If i close it, well all the stuff simply disappears, as if the program came to a stop. I loose all the title bars, etc.

Opening another terminal and typing ex. compiz --replace gives me that stuff:


breezier@breezier-rig:~$ compiz --replace -c emerald
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1152x864) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (bicubic) - Fatal: GL_ARB_texture_float not supported. This can lead to visual artifacts.

I seen around that i may need to install Xgl -- but how? and isnt Xgl an Nvidia setting?

thanx for help,

Breezier

---

### Post by tuxxy on 2008-12-29
You could either press ALT + F2 then enter the **emerald --replace** command in the box which appears, this allows you to run the command without opening a terminal window and will last for the whole session you are logged in.

Your best option if you want to use emerald all the time and dont fancy entering the command at every bootup is to open **system > prefs > sessions **and add emerald as a new session using the command emerald --replace

---

### Post by BreeZier on 2008-12-29
Now that's why :P

Thanks button pressed!

---

### Post by tuxxy on 2008-12-30
Glad its sorted out now, thanks for the thanks :lolflag:

---

### Post by akelsall on 2008-12-30
Thanks tuxxy.  I happened to stumble across your post when looking for others to help out. I've been having problems with Compiz not accurately displaying the border of windows (especially the top bar). This is great. No more disappearing title bars!!

Andy

---

### Post by tuxxy on 2008-12-30
hehe nice, glad you got your borders back too :D

---

### Post by Therion on 2008-12-30
edit...

---

