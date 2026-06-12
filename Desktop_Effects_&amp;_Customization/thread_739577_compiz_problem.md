---
title: "compiz problem"
date: 2008-03-29
forum: Desktop Effects &amp; Customization
---

### Post by jacob01 on 2008-03-29
when i try to enable compiz the screen flashes and then it returns me back to the desktop with the wobbly windows but without any other effect. So i run it from the command prompt and i find that xgl isnt present, so i install xserver-xgl (wich i have done before and has worked) but then when i restart my xserver i get a completely white screen and have to uninstall the xgl package in the terminal in order to see my desktop.

edit: i was able to just instal the xgl package when i was running my intel igp now with the nvidia card i get a white screen.

i get this
```
jacob@linux-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

### Post by ramkumail on 2008-03-30
For nvidia cards, You dont need xserver-xgl. 
Uninstall server-xgl
Go to restricted drivers manager and enable the graphics accelerater.
 It should ask you to restart your computer. do it.
This worked for me.
 If you have resuloution problems after it run "sudo dpkg-reconfigure xserver-xorg"
You might wonder without xserver how can one reconfigure it but may be xserver-xorg is installed in mine and that works.

---

### Post by jacob01 on 2008-03-30
i have the nvidia driver installed and every thing works good and the driver is enabled in the restricted drivers.

but what is causing this to do this i get wobbly windows and.... but not the differand desktop effect like cube

---

### Post by jacob01 on 2008-03-30
thanks any ways but i guess it was just some minor setting in the compiz manager :lolflag:

but now i have it fixed :)

---

### Post by ramkumail on 2008-04-03
Glad that you got it fixed.

---

