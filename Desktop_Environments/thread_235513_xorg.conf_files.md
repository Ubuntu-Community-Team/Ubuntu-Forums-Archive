---
title: "xorg.conf files ?"
date: 2006-08-13
forum: Desktop Environments
---

### Post by Magiczero on 2006-08-13
Hi, I am going to upgrade to DD 6.0.6.1 really soon.  I have a Hitachi Superscan Surpreme 21 and it requires that I run 1024x768 how do I edit my xorg.conf file so my monutor will work?  I have edited my xorg.conf file before for 6.06 and I forgot how!!  Can some help me?

I have another question, If I upgrade from a CD that I downloaded off the internet. Will everything I have on here be gone?

Thanks

---

### Post by chedabob on 2006-08-13
my personal way it to load up terminal then type

```

sudo gedit /etc/X11/xorg.conf

```

enter your admin password. then scroll to the bottom of Gedit. you should see a section called screen, that looks a little like this

```

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Monitor    "Acer AL1916W"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"

```

basically, remove any modes you dont want, and put the ones you do want in, so for you, you should probably delete everything except 1024x768, 800x600, and 640x480 (always good to leave some fallback ones in case one doesnt work).

do the same for all the lines, for all "default depth"

then just save, and reboot.

another way ive found, is to try updating your drivers. when i update my ATI drivers to the FGLRX drivers, my monitor is auto detected. i dont need to edit xorg.conf

---

### Post by Magiczero on 2006-08-13
Thanks I'll try that, How do I upgrade my dtivers?

---

### Post by chedabob on 2006-08-13
if you are using an ati, use this

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually)

---

### Post by Magiczero on 2006-08-13
It is an SIS card

---

### Post by chedabob on 2006-08-13
no idea.

theres a driver for XORG, but i cant find any install instructions. i would assume that it would be the same principle for all the drivers.

---

