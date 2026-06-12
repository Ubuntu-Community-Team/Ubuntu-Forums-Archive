---
title: "Display Resolution Issues Xubuntu 9.04"
date: 2009-07-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mudpark on 2009-07-09
[EDIT] Solved Problem Needed to add "HorizSync 31.50-50.00" to the Monitor section of my Xorg.conf file.  I installed Xubuntu onto an old Dell C600 Laptop. After installation it boots fine to the desktop but the display resolution is limited to 800x600. The Screen is physically capable of displaying well above 1024x768 but I only want to get the resolution to 1024x768. Also the computer has worked fine with previous versions of Ubuntu. 

 My computer is running an ATI Mobility M3 AGP graphics card.  I am using the default Xorg.conf file, and followed the instructions in the following thread, but after replacing the generic Xorg.conf file with the one from this post my computer rebooted giving me the error message saying  > &quot;Ubuntu is running in low graphics mode. (EE) Problem parsing the config file (EE) Error parsing the config file [http://georgia.ubuntuforums.org/showthread.php?t=828588&page=7](http://georgia.ubuntuforums.org/showthread.php?t=828588&page=7) 
 
 Every other custom Xorg.conf file I have tried has resulted in the same error message once the X server restarts. Also using the basic driver with Xorg results in minor vertical artifacts in the screen that are about 2cm wide and only run down one line when another program is open. I am wondering if I can switch to another driver besides the default &quot;ati&quot; driver that Xorg.conf uses, but this is only a minor problem and my major concern is getting &quot;1024x768&quot; resolution working at all.

---

### Post by Wolfskin75 on 2009-10-29
did you ever get this figured out?

---

