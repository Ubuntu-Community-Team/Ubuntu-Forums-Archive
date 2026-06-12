---
title: "Higan not detecting correct version of OpenGL"
date: 2016-03-01
forum: Emulators
---

### Post by brannon2 on 2016-03-01
Hi,

I'm a new user to Ubuntu, so I apologize in advance for any omissions or dumb questions. I'm running Ubuntu 14.04 64-bit on a brand new NUC5i3RYH, with 8 GB of Ram, an i3 quad core @2.1 Ghz, and Broadwell GT2 GPU. 

My question pertains to Higan--when I run it I get an error message saying "Error: OpenGL 3.2 is not available. Select another video driver on the Advanced Configuration tab and restart higan". When I run
```
glxinfo | grep version
```
I get:
```

server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.5.9
OpenGL core profile shading language version string: 3.30
OpenGL version string: 3.0 Mesa 10.5.9
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.5.9
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00

```
So, from what I understand this means I have OpenGL 3.3, which is a newer version than what Higan is looking for, right? In any case, if I override the version check with:
```
MESA_GL_VERSION_OVERRIDE=3.2 MESA_GLSL_VERSION_OVERRIDE=150 higan

```
Higan runs perfect, at 60fps, and no errors. So, my intuition would tell me that this is just a simple bug in the Higan code when it checks for the OpenGL version. Is there a way to manually fix this, or a way to force that override every time I open the program without having to go through the terminal to do it?

Thanks!

---

### Post by deadflowr on 2016-03-08
Add your override line to the desktop launcher for higan.
To do so, simply
Open the text editor, for Ubuntu that is gedit.
In gedit use the Open box and go to the file system, or Computer section.
Then go to the usr directory, then the share direcotory, and finally the applications directory.
Locate the higan desktop file; hopefully it should be listed.
Then simply change the line for Exec= to your override.

Now instead of simply saving it, as you won't be able to, choose the option to Save as and navigate to your Home section.
Here is the tricky part, the location you need to save as is in a hidden folder. to show hidden files and folder in gedit right click in the main window area.
When the hidden folders shows in the listings go to the folder marked .local. then go to the listing marked share. Then go to the section marked applications.
Now save.

the reason to do it this way is because files in your home folder are not affected by system updates, so the launcher will always persist regardless of updates.
(where as the file in applications will get overwritten any time an update comes through.)

Hope it makes sense, and works.

---

### Post by brannon2 on 2016-03-12
Thanks for the response! I tried the steps you laid out, and have run into another road block. After I saved the new higan.desktop file in the /home/.local/applications folder, I tried running Higan again, and got the same error message as before. I tried navigating to the new higan.desktop file in the file browser and running the file from there, and received this message: "The application launcher “higan.desktop” has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe." So, I tried right-clicking on the file and going into the properties. Under the permissions tab, I checked the box for "allow executing file as a program". When I try running it now, I get the message: "There was an error launching the application". 

Here's what my higan.desktop file looks like:
```
[Desktop Entry]
Name=higan
Comment=SNES emulator
Exec=MESA_GL_VERSION_OVERRIDE=3.2 MESA_GLSL_VERSION_OVERRIDE=150 higan
Icon=higan
Terminal=false
Type=Application
Categories=Game;Emulator;
Keywords=emulator;Nintendo;SNES;NES;Gameboy;Famicom;Super
```

What am I doing wrong here?

---

