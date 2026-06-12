---
title: "Compiz problems"
date: 2010-05-23
forum: Desktop Environments
---

### Post by Tylerlloll on 2010-05-23
Hi all, i just downloaded Ubuntu 10.04 yesterday and have it running in VMware player(Windows 7 host). This is the first linux OS i have ever used so sorry for being slow with this stuff. Im was trying to enable the normal Visual effects and it says desktop effects could not be enabled. I also tried to get Gnome Do to run and it says i need to enable compositing so i tried using the info from [http://ubuntu-tutorials.com/2009/02/25/update-enable-compositing-the-easier-way/](http://ubuntu-tutorials.com/2009/02/25/update-enable-compositing-the-easier-way/). It doesnt seem to do anything. And if i run compiz in my terminal in comes back with some stuff then freezes everything and i cant type anything so i have to restart or log off then log back in to do anything. Sorry if im not giving the right info or if some of this stuff shouldnt be here. Thanks in advance for any help. Let me know if you need more specific info.

This is what i get when i run compiz in terminal

compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

(metacity:2369): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

---

### Post by skarme on 2010-05-23
Which driver are you using?
and tell us abt your graphic chipset?
For now you may run compiz-check and see what the issue is.
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by Tylerlloll on 2010-05-23
heres the info i got from compiz-check


Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         VMware SVGA II Adapter
 Driver in use:         vmware
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [SKIP]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: Detected driver is not on the whitelist. 

Would you like to know more? (Y/n) y

 Your driver is not widely known to work with Compiz and thus may be
 blacklisted on certain distributions.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) n

---

### Post by skarme on 2010-05-23
"Your driver is not widely known to work with Compiz and thus may be
 blacklisted on certain distributions."
The above says it all my friends. Some drivers aren't compatible with compiz and as a result don't work. eg. openchrome driver
Compiz is just a check; it dosent install compiz or fiddle around with settings; I suggest you skip backlist checks and then post the complete output.

---

### Post by Tylerlloll on 2010-05-23
Ok, so this is what i get now. I thought the problem might be because i have another monitor in use so i disabled it and restarted Ubuntu. Now i get this.

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         VMware SVGA II Adapter
 Driver in use:         vmware
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

sorry for being a noob :(

---

### Post by skarme on 2010-05-24
Well the info here would help.
[http://ubuntuforums.org/archive/index.php/t-1018240.html](http://ubuntuforums.org/archive/index.php/t-1018240.html)
All the best. :)

---

### Post by Mistiq Dragon on 2010-10-13
I have no experience with vmware player whatsoever, but I know I installed 10.10 in Virtual Box today, and I needed to install Virtual Box Guest additions before the effects would work.  does Vmware player have anything like that?

---

