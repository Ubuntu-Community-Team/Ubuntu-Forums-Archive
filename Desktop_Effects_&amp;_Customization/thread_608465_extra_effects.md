---
title: "extra effects"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by Cedrick12 on 2007-11-10
I keep getting this message when I try to enable the extra effects...."Desktop effects could not be enabled"...what do I need to do to get this working correctly....I have a intel Graphics Media Accelerator X3100 by the way in a Dell inspiron 1420???

Can someone please help

---

### Post by creeco on 2007-11-10
Try opening the restricted drivers manager, and make sure that your intel driver is turned on!

---

### Post by Cedrick12 on 2007-11-10
yes this is what it says,  Intel(R) Pro/Wireless 3945 connection driver for linux is enabled and in use

---

### Post by kdawgmfic79 on 2007-11-10
is Composite enabled in your xorg.conf? Run
gksu gedit /etc/X11/xorg.conf

then add this if it is not in there

Section "Extensions"
	Option "Composite" "enable"
EndSection

---

### Post by mcduck on 2007-11-10
> **Cedrick12 said:**
> yes this is what it says,  Intel(R) Pro/Wireless 3945 connection driver for linux is enabled and in use

That driver is for your wireless network, not for your graphics card..

---

### Post by Forlong on 2007-11-10
There are no restricted drivers for intel graphics chips.

What's the output of ```
compiz
``` in a terminal?

---

### Post by Cedrick12 on 2007-11-10
for code compiz i get this

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

---

### Post by Forlong on 2007-11-10
Run Compiz like this and tell us how it works:
```
SKIP_CHECKS=yes compiz
```

---

### Post by Cedrick12 on 2007-11-11
that did not work this is what happened

ubuntu@ubuntu:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to connect to socket /tmp/dbus-ryVmf5MWAR: Connection refused
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by Forlong on 2007-11-11
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by TadH on 2007-11-11
#sudo

---

### Post by Cedrick12 on 2007-11-11
cedrick@cedrick-laptop:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1     Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2     Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1     Compiz configuration settings manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1     Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3     Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1     Compiz configuration system bindings

---

### Post by Cedrick12 on 2007-11-11
what did you mean by this "use the forum's CODE tag please (# button)"

---

### Post by Forlong on 2007-11-11
If you click on "Post Reply" there's a # button in the bar above the input field.


Packages are looking OK. There seems to be some troubles with dbus, though.
Try disabling or enabling the Dbus plugin (depending on what it is right now) in ccsm. Don't know if it helps but may be worth a try.

---

### Post by Cedrick12 on 2007-11-11
Ok How do I do that....Not sure where to go..

---

### Post by Forlong on 2007-11-11
Sorry, I somehow assumed you knew what I'm talking about.

ccsm is the CompizConfig Settings Manager - get it:
```
sudo apt-get install compizconfig-settings-manager
```
and run it via *System &#8594; Preferences &#8594; Advanced Desktop Effects Settings*

There you'll find the Dbus plugin I was referring to.

---

### Post by Cedrick12 on 2007-11-11
```
it still did not work got the same message "can not enable" 
```

---

### Post by TadH on 2007-11-11
isnt it sudo apt-get install compiz-config-settings-manager

---

### Post by Cedrick12 on 2007-11-11
i think so

---

### Post by Forlong on 2007-11-12
> **TadH said:**
> isnt it sudo apt-get install compiz-config-settings-manager
No.
> **Cedrick12 said:**
> it still did not work got the same message "can not enable"
Does it still complain about dbus when trying to run compiz in a terminal?

---

### Post by Cedrick12 on 2007-11-15
is the message that you are talking about 

cedrick@cedrick-laptop:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

---

### Post by Forlong on 2007-11-15
> **Forlong said:**
> Run Compiz like this and tell us how it works:
```
SKIP_CHECKS=yes compiz
```.

---

### Post by davydanko on 2008-02-03
hey, i have the same problem as cedrick. when i run
# compiz

i get this:
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

then i tried
# SKIP_CHECKS=yes compiz

i finally got awn up, but it lagged like crazy and didnt look right at all:confused: didn`t try any cubes, only want awn to work..anyone know what the problem is, or how i can fix it? thanks all:)


nvm, therse a reason it`s blacklisted:P but here is the thread u want cedrick :[http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112)

---

