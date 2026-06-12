---
title: "No title Bar in Beryl"
date: 2008-01-29
forum: Desktop Effects &amp; Customization
---

### Post by bigdog306smhs on 2008-01-29
OK i got Ubuntu feisty fawn and i got beryl installed and emerald installed to. and when i go to run beryl-manager my title bars go away i have looked and looked and everything that i try to do does not work here is what i get when i run beryl-manager in the terminal

**************************************************************
* Beryl system compatibility check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.4)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2046x2046)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.4)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2046x2046)

Reloading options
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011


and when i try to update the system it gives me this at the very end

Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages
  404 Not Found [IP: 80.77.247.17 80]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 3B in 1s (3B/s)  
Failed to fetch [http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 80.77.247.17 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

can i please have some help

Thanks, 
Bigdog306smhs

---

### Post by tangibleorange on 2008-01-29
Do you mean that your title bars are fine until you open the emerald settings manager?

Anyway, what happens if you just type:

> emerald

And if that does nothing:

> emerald --replace

---

### Post by bigdog306smhs on 2008-01-29
no if i switch the window manager to compiz the title bars come back. i just think that there is a problem with versions and that they are not compatible or something like that because every time i switch window managers it keeps saying in terminal this:

 beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011

i dont know what else to do

---

### Post by rnazario on 2008-01-29
I have somewhat of the same problem, the title bar disapears, the only way that I get it back is when I change everything to display no effects. I wonder if there is something in emerald that we can turn off to make the title bars come back.... but until then, looks like no wobbly windows for me...

---

