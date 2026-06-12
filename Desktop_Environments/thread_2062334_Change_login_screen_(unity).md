---
title: "Change login screen (unity)"
date: 2012-09-24
forum: Desktop Environments
---

### Post by agzathot on 2012-09-24
Hello guys i just install Ubuntu 12.04 (amd64) as dual boot on mine Alienware M11x, actually install severals times because issues with the video card (Optimus) i have a dual boot with Win7 Ultimate 64 and Ubuntu

I cant find a way to change my login wallpaped (dotted), i have try "ubuntu tweak" and dont change anything

already try changing direct on lightdm (unity-greeter.conf) but didnt work, i read on askubuntu that unity used your current background as login screen but isnt working for me 

Im a normal users trying linux i used redhat 4 LONG TIME ago and used only CLI no X11 :P

any tip about this ?

thanks in advance

----------------------------------
I think this covers my system information
----------------------------------

azathoth@Cthulu:~$ echo && date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && echo && /usr/lib/nux/unity_support_test -p -f || echo && dpkg -s mesa-utils && echo

Mon Sep 24 14:51:05 CDT 2012
Ubuntu 12.04.1 LTS
Linux 3.2.0-30-generic
unity 5.14.0

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 148
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: [http://mesa3d.sourceforge.net/](http://mesa3d.sourceforge.net/)

---

### Post by mcduck on 2012-09-25
Unity will use the same wallpaper as youa re using on your desktop, but the wall paper needs to be in the system-wide wallpaper directory (/usr/share/backgrounds) for that to work. LightDM can't access the wallpaper from inside the user's home directory.

I'm not sure about changing the login screen wallpaper manually, I'd assume unity-greeter.conf should do the trick but of course the same rule about the location of the image still applies.

---

### Post by kostkon on 2012-09-25
> **mcduck said:**
> Unity will use the same wallpaper as youa re using on your desktop, but the wall paper needs to be in the system-wide wallpaper directory (/usr/share/backgrounds) for that to work. LightDM can't access the wallpaper from inside the user's home directory.
LightDM can use whatever wallpaper the user has set, the only requirement being that the wallpaper just needs to be in the user's Pictures folder and the user has set the appropriate permissions for that folder, i.e. in the Permissions tab he/she has set the Folder Access for Others to Access Files and the hit the Apply Permissions to Enclosed Files button.

---

### Post by mcduck on 2012-09-25
OK, that's good to know. Does it work only for ~/Pictures, or also for subdirectories? (I have way too much images to dump them straight into Pictures...)

---

### Post by agzathot on 2012-09-25
ty kostkon & mcduck already set the permissions and works as shold

another question is it posible to set several pictures and ramdom see each 30 min a different background ?:confused:

---

### Post by newb85 on 2012-09-25
> **agzathot said:**
> another question is it posible to set several pictures and ramdom see each 30 min a different background ?:confused:

There are *many* ways of doing this.  I like the program Wallch.  It should be in the repositories.

---

### Post by agzathot on 2012-09-26
already install and configure Wallch, the main issue here was that i set the option to encript home folder, as far i have read on askubuntu and here :p

ty all for your help

---

### Post by newb85 on 2012-09-26
You could move these pictures somewhere not encrypted (outside your home directory) and create a symlink in the home folder for convenience.

Just a thought...

---

