---
title: "Compiz will not run when trying to use Cube plugin"
date: 2009-05-16
forum: Desktop Environments
---

### Post by Dimitriid on 2009-05-16
I am running 9.04 with the latest nvidia driver in the repository. Everything was working ok except one day I turned off the effects on the appearance menu.

I tried re-enabling them and they work. But as soon as I try to activate the cube plugin compiz stops. WHen I attempt to run it via the terminal this is what I get:

```
$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1360x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
libpng error: Read Error
Aborted
```

Now I ran the compiz-check and everything is ok. I tried to remove and reinstall all compiz packages and still have this issue. I also found this comment but I do not understand how you change those settings:

> The reason why my compiz/glxinfo wouldn't work is that the symlink to /usr/lib/xorg/modules/extensions/libglx.so was wrong. It was linked to an old and non-existant library installed in Hardy. I removed the symlink and created it again with the latest libglx.so.177.76 library. Now everything workes again.

Any ideas? Is not crucial as compiz otherwise works fine but I'd like to use the cube.

---

### Post by rflamini on 2009-05-25
I am having the same problem, when ever I try to use compiz it just stops at starting gtk-window-decorator. here is what it says:
rfg@RFG-laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (snow) - Info: Loaded Texture snowflake.png
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
Starting gtk-window-decorator

and it stays there.
I am running ubuntu 9.02 on a Dell Inspiron 1720 using intel graphics.
Please Help!!

---

### Post by Dimitriid on 2009-05-25
I partially resolved this by removing the skydome and caps. I later entered caps again and it continues to work, im guessing is related to the skydome.

---

### Post by Naizo on 2010-11-28
hi hi all ... i got the same problem ... can any1 tell me what to do  ? cuz i am  new at ubundu and cant do a lot of things :/

---

### Post by JaymoS on 2010-11-30
i am experiencing a similar problem but compiz is running just fine, including the cube plugin i am trying to get compiz to launch on startup by adding the command "compiz --replace" to Main Menu-->System-->Preferences-->Startup Applications but when i run it in terminal it says:

       PC:~$ compiz --replace
       compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

then hangs there and i have to use ctrl c to kill the proccess, which then messes up the top of my windows,but can be fixed by using Main Menu-->Other-->Compiz or starting compiz-fusion icon right clicking and selecting reload window manager

disabling skydome has no apparent effect on this message

i do have wallpaper plugin under utilities enabled, not sure if anyone else does

and i found this [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/549950](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/549950) but i have no idea how to "apply the attached patch" as it says

---

### Post by realzippy on 2010-11-30
*"....but i have no idea how to "apply the attached patch" as it says."*

Open cube.xml:

```
gksudo gedit /usr/share/compiz/cube.xml
```

Search for the line:

<default><value>[COLOR="Red"]/usr/share/gdm/themes/Human/ubuntu.png[/COLOR]</value></default>

and change it to:

<default><value>[COLOR="SeaGreen"]/usr/share/compiz/fusioncap.png[/COLOR]</value></default>

Close the file saving changes,done.

Edit:
If there is now an ugly shadow on the cube's top,edit the *fusioncap.png* file e.g. with gimp:
```
gksudo gimp /usr/share/compiz/fusioncap.png
```
Hit "edit",choose "clear",
hit "file",choose "save"....

---

### Post by JaymoS on 2010-11-30
Thanks realzippy that did it!  :D it still hangs in terminal, do you know why that is? is it just because compiz is still running?

---

### Post by realzippy on 2010-12-01
> **JaymoS said:**
> Thanks realzippy that did it!  :D it still hangs in terminal, do you know why that is? is it just because compiz is still running?

...what do you mean "hangs" ?
Run:

```
compiz --replace &
```

instead of

```
compiz --replace
```

---

### Post by JaymoS on 2010-12-07
i meant after i run 
```
compiz --replace
```the text insertion point indicator just blinks indefinitely but running
```
compiz --replace &
```works, it displays
```
 ~$ compiz --replace &
[1] 2279
```then returns to the shell prompt which allows me to exit terminal without messing up compiz

---

### Post by rebeccabunz on 2011-09-08
Thanks RealZippy I tried this and it worked great. I am officially in love with ubuntu forums :)

---

