---
title: "Compiz won't start"
date: 2008-12-22
forum: General Help
---

### Post by Mewshi on 2008-12-22
This is the output from running compiz --replace.

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

What's wrong?  How can I fix it?

---

### Post by gettinoriginal on 2008-12-23
Hope this helps:  :P

gksu gedit /usr/bin/compiz

then add your driver to the Driver whitelist section line #(54?)

as an example, mine says:

# For detecting what driver is in use, the + is for one or more /'s
XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"

if [ -x $METACITY ]; then
	FALLBACKWM="${METACITY}"
elif [ -x $KWIN ]; then
	FALLBACKWM="${KWIN}"
else
	FALLBACKWM=true
fi
FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"

---

### Post by Mewshi on 2008-12-23
My driver (i810) *is* listed...

This happened shortly after hooking up a second monitor...

---

### Post by gettinoriginal on 2008-12-23
ahhhhhhhhh, another monitor.  Check 2 things, Hardware Drivers to make sure your driver is activated and System > Appearance > Visual Effects to make sure that Extra or Custom is checked.

---

### Post by binbash on 2008-12-23
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/270122/comments/3](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/270122/comments/3)

---

### Post by Mewshi on 2008-12-23
I have tried both; it's an Intel chipset, so the driver is open, and should already be loaded.  When I go to 'Visual Effects' it says it couldn't start it :\

---

